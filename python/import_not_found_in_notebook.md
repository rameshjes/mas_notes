Sometimes when you install package from terminal and try to import in notebook, it does not work: 

Example: 

[Import on Jupyter notebook failed where command prompt works](https://github.com/jupyter/notebook/issues/1524)

# Possible Reason

Usually that indicates that the notebook is running with a different Python or in a different environment from Python in the command prompt. Check ``sys.executable`` to see which Python it's running in, and ``sys.path`` to see where it's looking for imports.

# Possible Solution

Install ipykernel in the environment, in which package is installed

```
workon env_name (in my case, it is **torch**)

# install ipykernel in that env.

/home/ramesh/virtualenvs/torch/bin/python -m pip install ipykernel

# install kernal with name
sudo /home/ramesh/virtualenvs/torch/bin/python -m ipykernel install --name torch
```

Now go to jupyter notebook, change kernel to ``torch``, and try importing package :) 
