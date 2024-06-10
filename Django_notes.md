# MVC - Model View Controller

## Overview
- **Client**: Sends requests.
- **Controller**: Intercepts user requests and coordinates with the view and model to send appropriate responses to the client.
- **Model**: Responsible for data definition, processing logic, and interaction with the backend database.
- **View**: Presentation layer.

```
Client ---- Controller -------
                |
              -------
              |   |
            View---Model---Database
```

## Django's MVT (Model View Template)
- **View**: Handles request and response (processing logic).
- **Template**: Returns HTML to the client (presentation layer).
- **Model**: Stores and retrieves data (data layer).

```
User---URL--View----Model,Template
```

- The URL dispatcher in Django is equivalent to the controller.

## Django Web Framework (Coursera)

### Commands
- Start a project: `django-admin startproject [projectname]`
- A Django project can have multiple apps.
- `manage.py`: Script inside the project with the same role as the `django-admin` utility. It is a local copy of the `django-admin` utility.

### Migration
- Refers to generating a database table whose structure matches the data model declared in the app.
- Django provides a ready-to-use admin interface through the `django-admin` utility.

## 3-Tier Architecture
1. **Presentation Tier**
2. **Application Tier**: Ties presentation to data.
3. **Data Tier**

## URL Patterns
- Django looks for URL patterns in the project directory to include the URLs from app `urls.py` using the `include()` function in `urls.py` of the project.

## Request Attributes
- `request.cookies`
- `request.files`
- `request.user`
- `request.has_key()`: Helps to check whether the GET or POST parameter dict has a value for a given key.

## HttpResponse Object
- `status_code`: Returns status code.
- `content`: Returns byte string of response.
- `__getitem__()`: Returns value of header.
- `__setitem__()`: Adds header.
- `write()`: Creates file-like object.

## URL Components
- `https://` is the scheme.
- `www` is the subdomain.
- **Domain**: Consists of second-level domain and top-level domain.
  - Second-level domain: Refers to the organization (e.g., GitHub).
  - Top-level domain: `.com`, `.org`, etc.

## Regular Expressions in Django URL
- Use `re_path` from `django.urls` library.
  - `^`: Start of string.
  - `$`: End of string.

## Error Handling in Django
- Use Django generic classes like `HttpResponseNotFound` to send error code 404.
- Raise exceptions using `Http404` exception.
- Create custom error pages.
- Django exception classes are defined in `django.core.exceptions`. Some important exceptions are:
  - `ObjectDoesNotExist`
  - `EmptyResultSet`
  - `FieldDoesNotExist`
  - `PermissionDenied`

## Request Handling
- When a view is called with POST or PUT request, the request body is populated by the form data.
- Django API defines various fields specific to the type of data stored (e.g., `EmailField`, `FileField`, `IntegerField`).
- These fields have built-in validators like `is_valid()` which return true if validators are passed.

## Class-Based Views
### Advantages
1. Respond to HTTP requests (GET, POST) with different class instance methods instead of using if-else in function views, helping in separating logic.
2. Implement OOP concepts.
3. Use mixins - class-based generic views, similar to multiple inheritance.

## Models
- **Application** -> **Model** -> **Database**
- Model acts as a single definitive source of information about your data.
- Contains all the essential fields and behavior of the database.
- Maps to a single database table.
- Attributes represent database fields.
- Use ORM (Object Relational Mapper) to map relational databases to objects represented as Django models.

## Migrations
- Records changes made to models and implements these changes to the database schema.

## Forms
- Django uses a `Form` class to assist developers with form creation and processing.
- Using the `Form` class, you can define all the expected attributes that the form will contain.
- The `Form` class is used to represent the expected attributes and render the form elements as HTML.

