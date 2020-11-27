

## Creating first project in Django

- First activate the virtual environment. Validate that the version of `pip` and `pip3` are same.
  You can validate using `pip --version` and `pip3 --version` commands. In the same way the output of
  `python3 --version` and `python --version` would also be same. Installing Django 
```bash
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


