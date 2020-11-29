
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