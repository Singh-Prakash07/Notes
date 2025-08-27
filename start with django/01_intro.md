# Django
  + Django is based on MVT(Model View Template). 
  + pip is a package installer for Python. we install django using pip.
  + But we can use other installer one of the is `uv` to install because of it's faster than pip
## To install django it's recommended to use virtual enviroment.
  + Virtual environments are isolated Python environments that allow you to install and manage packages without affecting your system-wide Python installation.
  ###  Using pip     
| OS| Window| Linux |
|---|---|---|
| Install vitual enviroment | `pip install virtualenv`| `pip3 install virtualenv` |
|create venv| `python -m venv .venv` | `python3 -m venv django_venv` |
|activate venv|`.venv\Scripts\activate` | `django_venv/bin/activate` |
|deactivate venv| `deactivate` | `deactivate` |
| Install django | `pip install django` | `pip install django` |
  ### using uv
install uv ` pip install uv` or `brew install uv`
create virutal enviroment `uv .venv`
to install a pakage eg. ` uv pip install django`. We can install all pakages by just adding prefix ` uv ` before command.
installing all pakage once from requirements.txt --> ` uv pip install -r requirements.txt`.

## Create project
| check version | `django-admin --version`| |


