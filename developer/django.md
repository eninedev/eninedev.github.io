# Django Style Guide

Table of Contents:

* [Settings](#settings)
  * [App Settings](#app-settings)
    * [Getting Started](#getting-started)
    * [Project-First Settings](#project-first-settings)
    * [App-First Settings](#app-first-settings)
    * [Data](#data)
  * [S3](#s3)
    * [S3 Settings](#s3-settings)
    * [Qux Cache](#qux-cache)
* [Models](#models)
  * [QuxModel](#quxmodel)
  * [Validation](#validation)
  * [Slugs](#slugs)
* [API](#api)
  * [Naming Convention](#naming-convention)
  * [Class-based  vs Function-based](#class-based-vs-function-based)

## Settings

Shared settings are defined at the project settings level and are Project-First. Examples include `DATA_DIR`

App settings are defined at the application level. These are settings that are unique to the app and are not shared settings.

### App Settings

All app settings must be prefixed with `<appname_>` explicitly. This is done to avoid namespace clashes.

Example: `ACME_LOOKBACK_PERIOD` is appropriate and ~`LOOKBACK_PERIOD`~ is verboten if `LOOKBACK_PERIOD` is an app setting for App `Acme`

[Top](#django-style-guide)

#### Getting Started

Using app settings

```python
from django.conf import settings
from . import settings as app_settings
```

Sample script to see what is defined in app_settings

```python
setting_objects = [x for x in dir(app_settings) if not x.startswith("_")]
for setting in setting_objects:
  print(f"{setting}: {getattr(app_settings, setting, None)}")
```

[Top](#django-style-guide)

#### Project-First Settings

Settings like `DATA_DIR` should be led by the project when available.

``` python
from django.conf import settings

S3_PREFIX = getattr(
  settings,
  "S3_PREFIX", 
  os.getenv("S3_PREFIX", None)
)
```

[Top](#django-style-guide)

#### App-First Settings

Settings that are uniquely app-first should use project settings if and only if app settings are unavailable.

``` python
from django.conf import settings

S3_PREFIX = os.getenv(
  "S3_PREFIX", 
  getattr(settings, "S3_PREFIX", None)
)
```

[Top](#django-style-guide)

#### Data

App level data directories are specified as `DATA_DIR/<appname>/<dirname>/` and are defined in the following order:

1. `settings.DATA_DIR`
2. Environment Variable `DATA_DIR`
3. `settings.BASE_DIR + "/data/"`
4. Undefined

``` python
from django.conf import settings

BASE_DIR = getattr(settings, "BASE_DIR", "/tmp")
DATA_DIR = os.path.join(BASE_DIR, "data/")
DATA_DIR = getattr(
  settings,
  "DATA_DIR", 
  os.getenv(
    "ACME_DATA_DIR", getattr(settings, DATA_DIR, None)
  )
)

DATA_DIR = os.path.join(DATA_DIR, "app_name") if DATA_DIR else "/dev/null"
```

[Top](#django-style-guide)

## S3

### S3 Settings

S3 Access Keys are defined consistently at the project level

- `AWS_S3_ACCESS_KEY`
- `AWS_S3_SECRET_ACCESS_KEY`

[Top](#django-style-guide)

#### Qux Cache

QWS defines an S3 cache defined at project level in `QWS_S3_CACHE_DIR` and allows locally cached S3 files to be shared across all apps.

[Top](#django-style-guide)

## Models

Django Models should be used to represent data - static and generated.

### QuxModel

All models will inherit from QuxModel to benefit from the methods that QuxModel supports including:

- Slugs
- `dtm_created`
- `dtm_updated`
- `to_dict()` which is a richer version of `model_to_dict()` and is on the instance itself.
- Built-in auditing

```python
class MyDataModel(QuxModel):
```

[Top](#django-style-guide)

### Validation

Django offers [four opportunities](https://docs.djangoproject.com/en/4.2/ref/models/instances/#validating-objects) for validation. 

[`full_clean()`](https://docs.djangoproject.com/en/4.2/ref/models/instances/#django.db.models.Model.full_clean) calls all four methods in this order and should inform you of the best place to put your validation methodology accordingly.

1. `clean_fields`
2. `clean`
3. `validate_unique`
4. `validate_constraints`

`full_clean()` is not called automatically and has to be called before `save()`

[Top](#django-style-guide)

### Slugs

QuxModel offers a builtin mechanism for automatically adding a unique slug to every instance. This is useful when objects are directly exposed to the user and is a preferred way of referencing objects without revealing information about the number of objects or the order of objects.

[Top](#django-style-guide)

## API

### Naming Convention

Use the following convention: `<Entity><Action>View`

Examples:
* `MyModelListView`, 
* `MyModelCreateView`, and 
* `MyModelLiveModeView`

[Top](#django-style-guide)

### Class-based vs Function-based

We prefer class-based API Views.

Class-based views are very easy to deploy for simple things because both Django and DRF have already done a lot of the heavy lifting.

Class-based views create a namespace where you can nest things like attributes and methods.

[Top](#django-style-guide)

