# Add jupyter kernel from notebook

1. Create virtual env using venv
```bash
python -m venv venv
```
or using virutalenv 
```bash
virtualenv venv
```
3. Install ipykernel to comunicate with jupyter notebook
```bash
./venv/bin/pip install ipykernel
```
3. Add venv to jupter notebook kernel
```bash
python -m ipykernel install --user --name=venv
```
4. check kernel creation
```bash
$ python -m ipykernel install --user --name=sensiml
/home/arch/.local/share/jupyter/kernels/sensiml
$ cat /home/arch/.local/share/jupyter/kernels/sensiml
{
 "argv": [
  "/home/arch/Documents/python/mypythonproject/venv/bin/python",
  "-m",
  "ipykernel_launcher",
  "-f",
  "{connection_file}"
 ],
 "display_name": "sensiml",
 "language": "python"
}
```

# Jupyter tips

~/.ipython/profile_default/ipython_config.py with the lines below.
```yaml
# Run all nodes interactively
c.InteractiveShell.ast_node_interactivity = "all"
```
