# Django Style Guide

Table of Contents:

* [Settings](#settings)
* [Models](#models)
  * [QuxModel](#quxmodel)
  * [Validation](#validation)
  * [Slugs](#slugs)
* [API](#api)
  * [Naming Convention](#naming-convention)
  * [Class-based  vs Function-based](#class-based-vs-function-based)

## Settings

Shared settings must sit at the project settings level.

App settings are defined at the application level. 

These are settings that are unique to the app and are not shared settings. 

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

### Validation

Django offers [four opportunities](https://docs.djangoproject.com/en/4.2/ref/models/instances/#validating-objects) for validation. 

[`full_clean()`](https://docs.djangoproject.com/en/4.2/ref/models/instances/#django.db.models.Model.full_clean) calls all four methods in this order and should inform you of the best place to put your validation methodology accordingly.

1. `clean_fields`
2. `clean`
3. `validate_unique`
4. `validate_constraints`

`full_clean()` is not called automatically and has to be called before `save()`

### Slugs

QuxModel offers a builtin mechanism for automatically adding a unique slug to every instance. This is useful when objects are directly exposed to the user and is a preferred way of referencing objects without revealing information about the number of objects or the order of objects.

## API

### Naming Convention

Use the following convention: `<Entity><Action>View`

Examples:
* `MyModelListView`, 
* `MyModelCreateView`, and 
* `MyModelLiveModeView`

### Class-based vs Function-based

We prefer class-based API Views.

Class-based views are very easy to deploy for simple things because both Django and DRF have already done a lot of the heavy lifting.

Class-based views create a namespace where you can nest things like attributes and methods.

