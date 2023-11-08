# [Developer Guide](index.md)

## Organizing project files

We use a standard layout for all django projects and apps.

### Project Layout

```
<django project>
├── README.md
├── manage.py
├── requirements.txt
├── apps
│   ├── __init__.py
│   ├── <django app>
│   └── <django app>
├── common
│   ├── css
│   │   └── site.css
│   ├── js
│   │   └── site.js
│   └── logo
│       ├── logo.png
│       └── logo.svg
├── project
│   ├── __init__.py
│   ├── asgi.py
│   ├── wsgi.py
│   ├── celery.py
│   ├── finders.py
│   ├── urls
│   │   ├── __init__.py
│   │   └── urls.py
│   └── settings
│       ├── __init__.py
│       └── settings.py
└── templates
    └── _blank.html
```

### Application Layout

```
<django app>
├── README.md
├── __init__.py
├── admin.py
├── apps.py
├── forms
│   ├── __init__.py
│   └── forms.py
├── models
│   ├── __init__.py
│   └── models.py
├── serializers
│   └── __init__.py
├── settings.py
├── templates
│   └── quxapp
│       └── base.html
├── tests
│   ├── __init__.py
│   └── tests.py
├── urls
│   ├── __init__.py
│   ├── apiurls.py
│   └── appurls.py
└── views
    ├── __init__.py
    ├── apiviews.py
    ├── appviews.py
    └── shared.py
```