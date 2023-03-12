# setup

Usually I use docker to run different versions of software because I have trouble remembering the different commands for version/env managers but I'm going to try using venvs for python.

The python (python3) version included with my linux distro is actually a fairly recent version (3.10.6) so I probably am ok to just use that for now.

I'm adding venv so that (libraries/packages?) don't conflict with one another across projects. Maybe in the future I'll add another python version which might require another file here but for now let's focus on venv.

I'm not sure if this was always the case but it looks like venv is packaged with python by default. `-m` runs a module in python so `python3 -m venv` runs venv.

I run 

```python3 -m venv .venv``` 

to create a new virtual environment in my directory. This creates a folder `./venv` (which apparently can have any name you specify, `.venv` is just a conventional name and is also hidden)

hmm looks like I need to install something

```
The virtual environment was not created successfully because ensurepip is not
available.  On Debian/Ubuntu systems, you need to install the python3-venv
package using the following command.

    apt install python3.10-venv

You may need to use sudo with that command.  After installing the python3-venv
package, recreate your virtual environment.
```

Looks like I need to install this package to install venv. Not sure if there's a better way of doing this but let's just follow this for now.

```sudo apt install python3.10-venv```

Looks like this worked

running `python3 -m venv .venv` after produced results

Can turn on venv by running `source .venv/bin/activate` a.k.a. `. .venv/bin/activate` and deactivate the env with `deactivate`