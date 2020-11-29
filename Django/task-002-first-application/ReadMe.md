## Let's crete our first Django application

- First navigate to the `first_project` directory. 
  You can create a simple application with following command. 
```bash
python manage.py startapp first_app
```

### Process of creating a view and mapping it to a URL

- First add you new app `first_app` to the list of `INSTALLED_APPS` in `./first_project/settings.py`

```python
INSTALLED_APPS = [
  'django.contrib.staticfiles',
  'first_app'
]
```

- Now run the server again and ensure that you are not getting any errors
```bash
python manage.py runserver
```

- Now we will try to add our first view in `first_app/views.py`. Add the following content to `views.py`
```python
from django.http import HttpResponse

def index(request):
    return HttpResponse("Hello World!")
```

- Now we will map this view to `urls.py` file.

```python
from first_app import views
from django.conf.urls import url
urlpatterns = [
    url(r'^$',views.index,name='index'),
]
```

- Now again run the server and visit `http://127.0.0.1:8000/`. You should be able to see the "Hello World!" 
  output.
  
![](https://github.com/codeaprendiz/_assets/blob/master/html-css-kitchen/django-task2-hello-world.png)  

### Files in project and their description

- admin.py
    - You can register your models here which Django will then use them with Django's admin interface.
- apps.py
    - Here you can place application specific configurations
- models.py
    - Here you store the application's data models
- tests.py
    - Here you can store test functions to test your code
- views.py
    - This is where you have functions that handle requests and return responses.
- Migrations folder
    - This directory stores database specific information as it relates to the models.            