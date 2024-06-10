
# Coursera API Documentation

## HTTP Requests

### Components of an HTTP Request
- **Version Type**
- **URL**
- **Method**: GET, POST, PUT, PATCH, DELETE
- **Request Headers**: Cookies, User-Agent, Referrers
- **Body** (optional): Cannot send body parameters in GET request

### Components of an HTTP Response
- **Requested Resource**
- **Content Length**
- **Content Type**
- **Headers**
- **ETags**
- **Time Last Modified**
- **HTTP Status Code**

## REST Architecture

### Definition
REST stands for Representational State Transfer. It is an architectural style for designing APIs that are scalable and provide a uniform interface between components.

### Constraints for a RESTful API
1. **Client-Server Architecture**
2. **Stateless**: The server does not maintain any state of the API client.
3. **Cacheable**
4. **Layered System**
5. **Uniform Interface**
6. **Code on Demand** (optional)

## Naming Conventions

### URI (Uniform Resource Identifiers)
- Use lowercase and hyphens.
- Use camelCase for variables.
- Use forward slashes to show hierarchy.
- Represent resources with nouns (avoid verbs).

### Examples
- Avoid file name extensions in your API: `https://orders.json`
- Use query string parameters for output format: `https://orders?format=json`
- No trailing slashes: `https://example.com/resource`

## cURL

### Usage
- **GET Request**: `curl <url>`
- **POST Request**: `curl -d "request body" -X POST <url>`

### Free Service
- [httpbin.org](https://httpbin.org): A free service to test HTTP requests.

## REST API Best Practices
1. **KISS (Keep It Simple Stupid)**: Do not perform too many tasks with one API.
2. **Filtering, Ordering, Pagination**: Deliver data in smaller chunks.
3. **Versioning**
4. **Caching**
5. **Rate Limiting**
6. **Monitoring**

## API Security

### Techniques
1. **SSL (Secure Socket Layer)**: Encrypts data for secure transmission.
2. **Signed URL**: Limited access to specific resources for a brief period.
3. **Token-Based Authentication**: JWT tokens over HTTP-based authentication.

### Common HTTP Status Codes
- **400**: Bad Request
- **401**: Unauthorized (username/password mismatch)
- **403**: Forbidden (user lacks authority)

### Additional Security Measures
- **CORS (Cross-Origin Resource Sharing)**
- **Firewalls**

## Authentication vs Authorization

- **Authentication**: Access
- **Authorization**: Authority after access

## Mock API

- **Definition**: Imitates real API endpoints with fake data.
- **Purpose**: Ensures the data structure remains correct.

## Django REST Framework (DRF)

### Overview
- A toolkit built on top of Django for building Web APIs.
- **Serialization**: Converts database models to JSON.

### Installation
```bash
pip install djangorestframework
```

### Configuration
- Add `'rest_framework'` to `INSTALLED_APPS` in `settings.py`.

### Features
- **Response Class**: Provides better responses than the standard `HttpResponse`.
- **api_view Decorator**: Provides a browser view of the API.
- **Throttling and Rate Limiting**
- **Authentication**

## Django Debug Toolbar

### Configuration
- Add to `INSTALLED_APPS` and `MIDDLEWARE` in `settings.py`.
- Add `INTERNAL_IPS = ['127.0.0.1']` in `settings.py`.
- Add to `urls.py`.

## DefaultRouter

- Comes with all the benefits of a `SimpleRouter` and creates a root API endpoint automatically.

## Model Serializer

- **Relationship Serializer**: Efficiently loads related models in a single SQL call.

## Filtering

- **Library**: `django-filter`
- **Usage**: Implement filtering, ordering, and sorting with class-based views.

## Data Validation in Django

### Methods
1. **Condition on Field**
2. **extra_kwargs**
3. **validate_field() Method**
4. **validate() Method**
5. **UniqueValidator and UniqueTogetherValidator**: Prevent duplicate fields.

## Data Sanitization

- **Definition**: Cleaning data from potential threats.
- **Library**: `bleach`

## Caching

- **Layered API Infrastructure**:
  - Visitor
  - Firewall
  - Reverse Proxy Server
  - Web Server
  - Database Server

## Throttling

- **Definition**: Prevents API abuse by limiting the number of times an API can be accessed in a given time frame.

## Djoser Library

- Simplifies authentication tasks.

## JWT Tokens

### Library
- `djangorestframework-simplejwt`

### Tokens
1. **Access Token**
2. **Refresh Token**

- **Usage**: The access token is used for authentication but expires after some time. The refresh token is used to generate a new access token.
