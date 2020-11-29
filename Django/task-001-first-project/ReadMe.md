

## Creating first project in Django

- First activate the virtual environment. Validate that the version of `pip` and `pip3` are same.
  You can validate using `pip --version` and `pip3 --version` commands. In the same way the output of
  `python3 --version` and `python --version` would also be same. Installing Django 
```bash
virtualenv django-virtual-env -p python3
source django-virtual-env/bin/activate
pip install django
```

- Creating the first project in Django
```bash
django-admin startproject first_project
```

- Let's use manage.py now
```bash
cd first_project;
python manage.py runserver
```

- Now you can go to your browser and visit the following webpage `http//127.0.0.1:8000/`
  You should see your first webpage locally hosted on your computer now.

![](https://github.com/codeaprendiz/_assets/blob/master/html-css-kitchen/django-task-1.png)

### Files you see in the project and their description

- __init__.py
    - This is a blank Python script that due to its special name let's Python know that this directory 
      can be treated as a package
- setting.py
    - This is where you will store all your project settings
- urls.py
    - This is a python script that will store all URL patterns for your project. Basically the different
      pages of your web application.
- wsgi.py
    - This is a Python script that acts as the Web Server Gateway Interface. It will later on help us deploy
      our web app to production.            


### pip Dependencies
```bash
pip install django
```