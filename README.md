## Python Django Realtors Application

This is a full realtors web application containing realtors, listings etc. creating by following Brad Traversy's **Python Django Dev To Deployment** udemy course.

### Development Stages

#### Starting Commands

The following commands were run for initialization. **Documented for future reference**

```python
  # install dependencies
  pipenv install django
  # start project
  django-admin startproject btre .
  # run server
  python manage.py runserver
  # create pages app
  python manage.py startapp pages

```

##### Add app to settings

In the settings file add pages app under `INSTALLED APP` as `pages.apps.PagesConfig`, `PagesConfig` is from `pages` folder in `apps.py`

##### Create a urls file in pages folder

Create a `urls.py` file inside the `pages` folder. Inside the `urls.py` file

```python

# pages/urls.py
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='index')
]

```

Go to main app inside the `urls.py` file and add the code below

```python

# btre/urls.py
from django.contrib import admin
from django.urls import path, include #import include

urlpatterns = [
    path('', include('pages.urls')), # add this line of code
    path('admin/', admin.site.urls),
]


```

Inside views file

```python
# pages/views.py
from django.shortcuts import render
from django.http import HttpResponse


# Create your views here.
def index(request):
    return render(request, 'pages/index.html')


def about(request):
    return render(request, 'pages/about.html')

```

Adding templates to be rendered in views functions add the following line of code in `settings.py file`

```python

  # in templates list under DIRS
  TEMPLATES = [
    'DIRS': [
            os.path.join(BASE_DIR, 'templates')
        ],
  ]

```
