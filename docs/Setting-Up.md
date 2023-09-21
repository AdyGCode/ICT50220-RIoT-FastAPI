# Setting Up

Create a new folder, create a Python virtuak environment, install FastAPI dependencies

> *NOTE:* Personally I like to name my virtual environments based on the operating system and location.
> For example, `venv-mac`, `venv-306` etc.
```shell
mkdir ICT50220-RIoT-FastAPI
cd ICT50220-RIoT-FastAPI
pip install virtualenv
python -m venv venv
```
Activate the virtual environment:
#### Windows:
```shell
.\venv\Scripts\activate
```

#### MacOS/Linux: 
```shell
source ./venv/bin/activate
```

Now we can install the other required packcages:

```shell
pip install 'fastapi[all]'
```

This is the FastAPI Python package and the various other related packages.
This includes the `uvicorn` server that will be used in developing the code.

## Create a Simple `main.py` application

Create  new main.py in the root of your project

Add the following code:
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

We will explain how it works in a moment... first lets check it works.

## Running Uvicorn

Open a second terminal, and make sure you are int he correct folder... plus activate the virtual environment:

Windows:
```shell
cd ICT50220-RIoT-FastAPI
.\venv\Scripts\activate
```

Mac/Linux:
```shell
cd ICT50220-RIoT-FastAPI
source ./venv/bin/activate
```

Now run uvicorn using:
```shell
uvicorn main:app --reload
```

In my development environment I get the following shown from the command line:

![](documentation/images/3711f60c.png)

It shows you where the API will be serviced from, 127.0.0.1:8000 (IP Address and Port).

Now open a browser and visit: http://127.0.0.1:8000

If you get a different address shown, you should use that...

Here is a picture of the output from the Browser:

![](documentation/images/10992885.png)

This shows success.


### About that Uvicorn command

The command `uvicorn main:app` has three parts:

- `main`: the file `main.py` (the Python "module").
- `app`: the object created inside of `main.py` with the line `app = FastAPI()`.
- `--reload`: make the server restart after code changes. Only use for development.

## What's next

In the Documentation you will find a set of documents giving stages of development of a small API and also Web Interface using FastAPI and Jinja2.

- [Documentation](../docs)

The next step is [Basics](Basics.md).
