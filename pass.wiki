# Password management

## Initiate gpg-agent

* Import gpg keys

```
gpg --import XX.gpg
gpg --import XX.asc
```

* Copy conf

```
cp ~/.dotfiles/gpg-agent.conf .gnupg/gpg-agent.conf
```

* Trust key

```
gpg --edit-key B212E65B trust quit
```

## pass

*pass* is a simple password manager from the command line based on GPG. You can 
initiate using

```
pass init B212E65B
```

Create a password for your email account(s):

```bash
$ pass insert Mail/account
```

