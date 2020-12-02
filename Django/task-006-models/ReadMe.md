## Models

```bash
python manage.py migrate
```

Now to register the changes to your app
```bash
python manage.py makemigrations app1
```

Inorder to fully use the database and the Admin, we will need to create "superuser"
```bash
python manage.py createsuperuser
```

- First we need to write to our `first_app/modules.py` class to add the models
```python
from django.db import models
class Topic(models.Model):
    top_name = models.CharField(max_length=264, unique=True)

    def __str__(self):
        return self.top_name

class Webpage(models.Model):
    topic = models.ForeignKey(
        Topic,
        on_delete=models.CASCADE,
    )
    name = models.CharField(max_length=264, unique=True)
    url = models.URLField(unique=True)

    def __str__(self):
        return self.name

class AccessRecord(models.Model):
    name = models.ForeignKey(
        Webpage,
        on_delete=models.CASCADE,
    )
    date = models.DateField()

    def __str__(self):
        return str(self.date)
```

- Now run the migrations using following command
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

- Now to register the changes to our application
```bash
$ python manage.py makemigrations first_app
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, first_app, sessions
Running migrations:
  Applying admin.0003_logentry_add_action_flag_choices... OK
  Applying auth.0009_alter_user_last_name_max_length... OK
  Applying auth.0010_alter_group_name_max_length... OK
  Applying auth.0011_update_proxy_permissions... OK
  Applying auth.0012_alter_user_first_name_max_length... OK
```

- Now run the `migrate` command once again
```bash
$ python manage.py migrate
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, first_app, sessions
Running migrations:
  Applying first_app.0001_initial... OK
```

- Now let's interact with the database using the following
```bash
$ python manage.py shell
>>> from first_app.models import Topic
>>> print(Topic.objects.all())
<QuerySet []>
>>> t=Topic(top_name="Social Network")
>>> t.save
>>> print(Topic.objects.all())
<QuerySet [<Topic: Social Network>]>
```

- Now we need to register our new models in the `admin.py` file.
```python
from django.contrib import admin

# Register your models here.

from first_app.models import Topic,Webpage,AccessRecord
admin.site.register(Topic)
admin.site.register(Webpage)
admin.site.register(AccessRecord)
```

- Now we will create a super user to interact with the admin interface
```bash
$ python manage.py createsuperuser
Username (leave blank to use 'ankitsinghrathi'): admin
Email address: a**************@gmail.com
Password: 
Password (again): 
Superuser created successfully.
```

- Now start the server again and visit [http://127.0.0.1:8000/admin](http://127.0.0.1:8000/admin). 
  Type the username and password you just created for the superuser.

![](https://github.com/codeaprendiz/_assets/blob/master/html-css-kitchen/django-admin-interface.png)

