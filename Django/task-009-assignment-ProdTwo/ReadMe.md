
```bash
$ django-admin startproject ProTwo
```

```bash
$ python manage.py startapp appTwo
```

```bash
$ mkdir -p  templates/appTwo
$ touch templates/appTwo/index.html
$ touch templates/appTwo/users.html
```

- Now edit the `settings.py` file and add the following in addition what is already present
  - Add `TEMPLATE_DIR`
  - Add `appTwo` to the list of INSTALLED_APPS
  - Add `'DIRS': [TEMPLATE_DIR, ],` 
```python
from pathlib import Path
import os

BASE_DIR = Path(__file__).resolve().parent.parent
TEMPLATE_DIR = os.path.join(BASE_DIR, 'templates')


INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'appTwo'
]


TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [TEMPLATE_DIR, ],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```

- Now we will start editing the models
```python
from django.db import models


# Create your models here.
class User(models.Model):
    first_name = models.CharField(max_length=128)
    last_name = models.CharField(max_length=128)
    email = models.EmailField(max_length=254,unique=True)
```

- Now edit the `views.py` file
```python
from django.shortcuts import render
from django.http import HttpResponse
from appTwo.models import User
# Create your views here.

def index(request):
    return render(request,'apptwo/index.html')

def users(request):

    user_list = User.objects.order_by('first_name')
    user_dict = {"users":user_list}
    return render(request,'apptwo/users.html',context=user_dict)
```

- Now we will set up the `urls.py` file of `appTwo`
```python
from django.conf.urls import url
from appTwo import views

urlpatterns = [
    url(r'^$', views.users, name='users'),
]
```

- Now include above urls.py file in the project `urls.py` file
```python
from django.conf.urls import url
from django.contrib import admin
from django.urls import path
from django.conf.urls import include
from appTwo import views

urlpatterns = [
    url(r'^$', views.index, name='index'),
    url(r'^users/', include('appTwo.urls')),
    path('admin/', admin.site.urls),
]
```

- Lets run the migrations now
```bash
$ python manage.py migrate   
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying admin.0003_logentry_add_action_flag_choices... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying auth.0008_alter_user_username_max_length... OK
  Applying auth.0009_alter_user_last_name_max_length... OK
  Applying auth.0010_alter_group_name_max_length... OK
  Applying auth.0011_update_proxy_permissions... OK
  Applying auth.0012_alter_user_first_name_max_length... OK
  Applying sessions.0001_initial... OK
```

- Now we need to register these changes to our application appTwo
```bash
$ python manage.py makemigrations appTwo
Migrations for 'appTwo':
  appTwo/migrations/0001_initial.py
    - Create model User
```

- Now run the migrations one more time
```bash
$ python manage.py migrate              
Operations to perform:
  Apply all migrations: admin, appTwo, auth, contenttypes, sessions
Running migrations:
  Applying appTwo.0001_initial... OK
```

- Now since we would be using the admin interface, lets go to `admins.py` file and
```python
from django.contrib import admin
from appTwo.models import User
# Register your models here.
admin.site.register(User)
```

- Now lets run the server and check. You will get a blank screen on the browser which is expected.
```bash
$ python manage.py runserver
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).
December 02, 2020 - 13:37:47
Django version 3.1.3, using settings 'ProTwo.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```

- Lets create a superuser to login to admin page
```bash
$ python manage.py createsuperuser
Username (leave blank to use 'ankitsinghrathi'): admin
Email address: a***************1@gmail.com
Password: 
Password (again): 
The password is too similar to the username.
Superuser created successfully.
```

- Add following to index.html
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Home</title>
  </head>
  <body>
    <h1>Welcome!</h1>
    <h2>Go to /users to see the list of user information!</h2>

  </body>
</html>
```
- Add the following to `users.html` 
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Users</title>
  </head>
  <body>
    <h1>Here are your users:</h1>

    {% if users%}

    <ol>
      {% for person in users %}
      <li>User Info</li>
        <ul>
          <li>First Name: {{person.first_name}}</li>
          <li>Last Name: {{person.last_name}}</li>
          <li>Email: {{person.email}}</li>
        </ul>
        {% endfor %}
    </ol>




    {% endif %}
  </body>
</html>
```

- Lets populate the database now using `populate_users.py`
```python
import os
# Configure settings for project
# Need to run this before calling models from application!
os.environ.setdefault('DJANGO_SETTINGS_MODULE','ProTwo.settings')

import django
# Import settings
django.setup()

import random
from appTwo.models import User
from faker import Faker

fakegen = Faker()

def populate(N=5):
    '''
    Create N Entries of Dates Accessed
    '''

    for entry in range(N):

        # Create Fake Data for entry
        fake_name = fakegen.name().split()
        fake_first_name = fake_name[0]
        fake_last_name = fake_name[1]
        fake_email = fakegen.email()

        # Create new User Entry
        user = User.objects.get_or_create(first_name=fake_first_name,
                                          last_name=fake_last_name,
                                          email=fake_email)[0]


if __name__ == '__main__':
    print("Populating the databases...Please Wait")
    populate(20)
    print('Populating Complete')

```

- Run the file for populating the database
```bash
$ python populate_users.py    
Populating the databases...Please Wait
Populating Complete
```

- Now run the server again and see the results

![](https://github.com/codeaprendiz/_assets/blob/master/html-css-kitchen/django-assignment-ProTwo.png)

![](https://github.com/codeaprendiz/_assets/blob/master/html-css-kitchen/django-assignment-ProTwo-userspage.png)

![](https://github.com/codeaprendiz/_assets/blob/master/html-css-kitchen/django-assignment-ProTwo-adminpage-users.png)

![](https://github.com/codeaprendiz/_assets/blob/master/html-css-kitchen/django-assignment-ProTwo-adminpage-user-details.png)