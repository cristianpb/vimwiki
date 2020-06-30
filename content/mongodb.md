# Mongodb  

Mongodb is able to query values inside arrays and not only match strings or intigers.

# Projection

> Describe the shape that we want the documents to take in the query.

```
query = {"manufacturer": "Toyota"}
projection = {"_id": "0", "name": 1}
autos = db.autos.find(query, projection)
```

# mongoimport
`mongoimport -d dbname -c collectionname --file input-file.json`

# operators, staring by "$"
Inequality operators:
    * ($gt, $lt, $gte, $lte, $ne)
    * example:
        * `query = {"population" : {"$gt": 5000}}`
        * `query = {"population" : {"$gt": 5000, "$lt": 1000}}`
        * City names starting by X: `query = {"name" : {"$gte": 'X', "$lt": 'Y'}}`
        * Date between: `query = {"dounfing date" : {"$gt": datetime(1890,1,1), "$lte": datetime(1900,1,1)}}`

## Regex operator

- Base on PCRE (perl compatible regular expression library)
- Regular expresion queries

```
db.cities.find({"motto": {"$regex" : "friendship"}}).count()
db.cities.find({"motto": {"$regex" : "[Ff]riendship"}}).count()
db.cities.find({"motto": {"$regex" : "[Ff]riendship|[Hh]appiness"}}).count()
```

## In operator

Allow to specify an array of values possible for the query

```
db.autos.find("modelyears": {"$in": [1958, 1966, 1967]})
```

## all operator

The query values must contain **all** this values in order to be retrieved:

```
db.autos.find("modelyears": {"$all": [1958, 1966, 1967]})
```

## Dot notation

You can dig in into properties using dot notation.

db.tweets.find({"entities.hashtags": {"$ne" : []}},  {"entities.hashtags.text" : 1, "id" : 0})

# Updates

```
city = db.cities.findOne({"name": "munchen", "country": "germany"})
city['isoCountryCode'] = 'DEU'
db.cities.save(city)
```

* update expects a query document as is first parameter, and an update parameter as a second parameter
* if we dont use set or unset the document will be replaced.

**Set**:
If the document does not already contains the specified parameter, then that field should be added.

```
city = db.cities.update({"name" : "munchen", "country" : "germany"}, {"$set" : {"isoCountryCode": "DEU"}})
```

**Unset**
What ever documents that are dound in the query and if they contains the field, then remove it.

```
city = db.cities.update({"name" : "munchen", "country" : "germany"}, {"$unset" : {"isoCountryCode": ""}})
```

# Remove documents

**drop**: remove the entire collections
db.cities.drop()

**remove**: 
remove the cities containing chicago: `db.cities.remove({"name":"Chicago"})`
remove cities that doesnt have a name: ` db.cities.remove({"name": { "$exist" : 0}})`

# Shell

> To start shell `mongo`

```
use examples
db.cities.find()
db.cities.find({"gouvermentType": {"$exists" : 1}})
db.cities.find({"gouvermentType": {"$exists" : 1}}).count()
db.cities.find({"gouvermentType": {"$exists" : 1}}).pretty()
```

# Aggregation framework

Provides some builtin data analysis tools for using mongodb.

* Example: Grouping tweets by user and count the number of tweets for each user.
Use the aggregator sum to add 1 for each value.

```
results = db.tweets.aggregate([{"$group" : {"_id" : "$user.screen_name",
                                "count": { "$sum" : 1}}},
                               { "$sort":  { "count" : -1}} ])
```

## Example for tweeter source

```
#!/usr/bin/env python
"""
The tweets in our twitter collection have a field called "source". This field describes the application
that was used to create the tweet. Following the examples for using the $group operator, your task is 
to modify the 'make-pipeline' function to identify most used applications for creating tweets. 
As a check on your query, 'web' is listed as the most frequently used application.
'Ubertwitter' is the second most used. The number of counts should be stored in a field named 'count'
(see the assertion at the end of the script).

Please modify only the 'make_pipeline' function so that it creates and returns an aggregation pipeline
that can be passed to the MongoDB aggregate function. As in our examples in this lesson, the aggregation 
pipeline should be a list of one or more dictionary objects. 
Please review the lesson examples if you are unsure of the syntax.

Your code will be run against a MongoDB instance that we have provided. 
If you want to run this code locally on your machine, you have to install MongoDB, 
download and insert the dataset.
For instructions related to MongoDB setup and datasets please see Course Materials.

Please note that the dataset you are using here is a smaller version of the twitter dataset 
used in examples in this lesson. 
If you attempt some of the same queries that we looked at in the lesson examples,
your results will be different.
"""


def get_db(db_name):
    from pymongo import MongoClient
    client = MongoClient('localhost:27017')
    db = client[db_name]
    return db

def make_pipeline():
    # complete the aggregation pipeline
    pipeline = [{"$group" : {"_id" : "$source", "count": { "$sum" : 1}}},
                               { "$sort":  { "count" : -1}} ]
    return pipeline

def tweet_sources(db, pipeline):
    return [doc for doc in db.tweets.aggregate(pipeline)]

if __name__ == '__main__':
    db = get_db('twitter')
    pipeline = make_pipeline()
    result = tweet_sources(db, pipeline)
    import pprint
    pprint.pprint(result[0])
    assert result[0] == {u'count': 868, u'_id': u'web'}
```

## operators

[More operators](https://docs.mongodb.com/manual/reference/operator/aggregation/project/#pipe._S_project)

* "$project": select the field that we want in the next stage of the pipeline
    * include fields from the original document
    * insert computed fields
    * rename fields
    * create fields that hold 

* "$match" : Subset documents from the initial ones
* "$group"
* "$sort"
* "$skip": skip a number of documents at the beginning of the search
* "$limit": limit the number of selected documents
* "$unwind": break the field values that are composed by arrays in to individual documents.

```
results = db.tweets.aggregate([
    { "$match" : { "users.friends_count" : { "$gt" : 0},
                    "users.followers_count" : { "$gt" : 0}}},
    { "$project" : { "ratio" : { "$divide" : [ "$user.followers_count", "$user.friends_count"]},
                    "screen name": "$user.screen_name"}},
    { "$sort": { "ratio" :  -1}},
    { "$limit": 1}]) 
```

Find the number person in Brasilia timezone with more than 100 tweets and more followers

```
#!/usr/bin/env python
"""
Write an aggregation query to answer this question:

Of the users in the "Brasilia" timezone who have tweeted 100 times or more,
who has the largest number of followers?

The following hints will help you solve this problem:
- Time zone is found in the "time_zone" field of the user object in each tweet.
- The number of tweets for each user is found in the "statuses_count" field.
  To access these fields you will need to use dot notation (from Lesson 4)
- Your aggregation query should return something like the following:
{u'ok': 1.0,
 u'result': [{u'_id': ObjectId('52fd2490bac3fa1975477702'),
                  u'followers': 2597,
                  u'screen_name': u'marbles',
                  u'tweets': 12334}]}
Note that you will need to create the fields 'followers', 'screen_name' and 'tweets'.

Please modify only the 'make_pipeline' function so that it creates and returns an aggregation 
pipeline that can be passed to the MongoDB aggregate function. As in our examples in this lesson,
the aggregation pipeline should be a list of one or more dictionary objects. 
Please review the lesson examples if you are unsure of the syntax.

Your code will be run against a MongoDB instance that we have provided. If you want to run this code
locally on your machine, you have to install MongoDB, download and insert the dataset.
For instructions related to MongoDB setup and datasets please see Course Materials.

Please note that the dataset you are using here is a smaller version of the twitter dataset used 
in examples in this lesson. If you attempt some of the same queries that we looked at in the lesson 
examples, your results will be different.
"""

def get_db(db_name):
    from pymongo import MongoClient
    client = MongoClient('localhost:27017')
    db = client[db_name]
    return db

def make_pipeline():
    # complete the aggregation pipeline
    pipeline = [
    { "$match" : { "user.time_zone" : "Brasilia", 
                   "user.statuses_count" : {"$gte" : 100} } },
    { "$project" : { "_id" : 1, "screen_name": "$user.screen_name", 
                     "tweets" : "$user.statuses_count",
                     "followers": "$user.followers_count"} },
    { "$sort": { "followers" :  -1}},
    { "$limit": 1}
    ]
    #print(pipeline)
    return pipeline

def aggregate(db, pipeline):
    return [doc for doc in db.tweets.aggregate(pipeline)]


if __name__ == '__main__':
    db = get_db('twitter')
    pipeline = make_pipeline()
    result = aggregate(db, pipeline)
    #print(result)
    import pprint
    pprint.pprint(result)
    assert len(result) == 1
    assert result[0]["followers"] == 17209
```

# Indexes

Faster query system:
```
db.osm.ensureIndex("tg" : 1)
```

Open Street maps, indexes coordinates (latitude and longitude), then it uses
`$near` operator to search locations near a certain point
