
### Using static assets

- Add the following to the `settings.py` file
```python
import os
from pathlib import Path
BASE_DIR = Path(__file__).resolve().parent.parent
STATIC_DIR = os.path.join((BASE_DIR, "static"))

STATICFILES_DIRS = [
    STATIC_DIR,
]
```

- Now run the server again and visit the static file using [http://127.0.0.1:8000/static/images/djangoguitar.jpg](http://127.0.0.1:8000/static/images/djangoguitar.jpg)

![](https://github.com/codeaprendiz/_assets/blob/master/html-css-kitchen/django-task5-static-files.png)


- Now lets try adding this image to html page. Add the following to `templates/first_app/index.html`
```html
<!DOCTYPE html>
{% load static %}
<html>
  <head>
    <meta charset="utf-8">
    <title>First App</title>
  </head>
  <body>
    <h1>Hi, this is a picture of Django himself!</h1>
    <img src="{% static "images/djangoguitar.jpg" %}" alt="Uh Oh, didn't show!">


  </body>
</html>
```

- Now run the server again and check `http://127.0.0.1:8000/`


![](https://github.com/codeaprendiz/_assets/blob/master/html-css-kitchen/django-static-files-part2.png)

- Now let's try to load static css files. Add the following to `static/css/mystyle.css`

```css
h1{
  color: red;
}
```

- Edit the `index.html` file and add the following
```html
<head>
  <meta charset="utf-8">
  <title>First App</title>
  <link rel="stylesheet" href="{% static "css/mystyle.css" %}"/>
</head>
```

![](https://github.com/codeaprendiz/_assets/blob/master/html-css-kitchen/django-static-part3.png)