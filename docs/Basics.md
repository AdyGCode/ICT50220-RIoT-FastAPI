# Basics

Let's just quickly look at the basics of the [main.py](../main.py) file we created.

```python
from fastapi import FastAPI

app = FastAPI()


@app.get("/")
async def root():
    return {"message": "Hello World"}


@app.get("/hello/{name}")
async def say_hello(name: str):
    return {"message": f"Hello {name}"}
```

- `app = FastAPI()` creates a new "app" object.
- `@app.get("/")` is a decorator that routes the request to "/" to the following method
- `async` allows FastAPI to run code asynchronously, thus it is able to have multiple requests waiting to be serviced and their responses sent back when ready.
- `@app.get("/hello/{name}")` tells the router to send the calls to '/hello/...' to the method that follows. More importantly the `{name}` is a parameter that may be passed as part of the URL, for example, `/hello/Adrian`.
- `async def say_hello(name: str):` is teh method called by the "/hello/..." route, with the `{name}` from the route matching the `name: str` in the parameter list. The `:str` is a type hint that makes FastAPI expect a string as the parameter.

One thing that is beautoful about FastAPI is that it generates API documentation automatically.

Visit the following location: `http://127.0.0.1:8080/docs` to see the current documentation. This is generated by Swagger UI [https://github.com/swagger-api/swagger-ui](https://github.com/swagger-api/swagger-ui).

An alternative set of documentation is available at `http://127.0.0.1:8000\redoc` which is provided by Redoc [https://github.com/Rebilly/ReDoc](https://github.com/Rebilly/ReDoc)

## The OpenAPI Standard and your API

The OpenAPI schema is what powers the two interactive documentation systems included.

You could also use the OpenAPI schema to generate code automatically, for clients that communicate with your API. For example, frontend, mobile or IoT applications.

FastAPI generates a "schema" with all your API using the OpenAPI standard for defining APIs.

| Component | Description |
|--------------|-----------------------------|
| "Schema" |   A "schema" is a definition or description of something. Not the code that implements it, but just an abstract description. |
| API "schema" | In this case, OpenAPI is a specification that dictates how to define a schema of your API. This schema definition includes your API paths, the possible parameters they take, etc. |
| Data "schema" | The term "schema" might also refer to the shape of some data, like a JSON content. In that case, it would mean the JSON attributes, and data types they have, etc. |
| OpenAPI and JSON Schema | OpenAPI defines an API schema for your API. And that schema includes definitions (or "schemas") of the data sent and received by your API using JSON Schema, the standard for JSON data schemas. |

By the way, you can see the actual JSON that forms the API defintion by visiting: [http://127.0.0.1:8000/openapi.json](http://127.0.0.1:8000/openapi.json).

## API Endpoints

The path at the end of the `http://DOMAIN/` in the call is known as an ENDPOINT. These endpoints are also called ROUTES.

They tend to have a method as part of the path which indicates a type of operatn that will be performed. 

Part of this is also how the request is made. These use HTTP Methods.

## APIs and HTTP Methods

The common four HTTP methods are:
- POST
- GET
- PUT
- DELETE

There are other HTTP methods that perform other purposes and they include:
- OPTIONS
- HEAD
- PATCH
- TRACE

The HTTP protocol provides the facility to communicate to each path using one (or more) of these "methods".

If we look at the above methods we are able to equate them to parts of what we know as CRUD or BREAD:

| CRUD | BREAD | HTTP Method | Purpose                                 | Decorator             |
|:----:|:-----:|:------------|:----------------------------------------|:----------------------|
|  C   | A     | POST        | used to Create resources/data           | `.post()`             |
|  R   | B R   | GET         | used to Read one or more resources/data | `.get()`              |
|  U   | E     | PUT / PATCH | used to update the resource/data        | `.put()` / `.patch()` |
|  D   | D     | DELETE      | used to removeresources/data            | `.delete()`           |

## The Methods and the Decorators

We saw in the small example how we create our endpoints and how we identify the methods being used.

This is via **decorators**.

```python
@app.get("/")
```
The `@app` refers to the `app` object, and identifies the method being listened for as `get` on the  `/` endpoint.

## The Handling Methods

The handling methods are what are called when a particular endpoint request is made.

They may be defined using `async def` or the plain `def`.

These have slightly different outcomes. More are https://fastapi.tiangolo.com/async/#in-a-hurry.


## Up next

Next we look at [Endpoints and Parameters](Endpoints-and-Parameters.md) in more detail.