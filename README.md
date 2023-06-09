# Usual setup

```bash
python3 -m venv .venv

source .venv/bin/activate

pip install flask
```

# Flask main stuff

Create "app.py"

```python
from flask import Flask, request

app = Flask(__name__)
```

Create a .flaskenv file and add the following

```
FLASK_APP=app
FLASK_DEBUG=1
```

# Run the server

```bash
flask run
```

This runs on port 5000

# Docker

## Create image

The last dot tells you where the Dockerfile is located

```bash
docker build -t <image_name> .

Example:
docker build -t flask-smorest-api .
```

## Run the image from command line

Port forwarding shown, the first ports show the value need on your local machine

```bash
docker run -p 8000:5000 <image_name>

Example:
docker run -p 8000:5000 flask-smorest-api
```

## Reload app that is running in docker image

-w -> docker folder

-v -> volume (where to find the code)

-d -> detach from terminal (run in background)

sh -c "command" -> will override the command in the docker file

```bash
docker run -dp 8000:5000 -w /app -v "${pwd}:/app" <image_name> sh -c "flask run --host 0.0.0.0"

Example:
docker run -p 8000:5000 -w /app -v "$(pwd):/app" flask-smorest-api sh -c "flask run --host 0.0.0.0"
```

# API

Checkout the api in
`http://localhost:8000/swagger-ui`

# Libraries used

- Marshmallow - validation
- Blueprint - split api into multiple segments


# Deployment
Webservice runs on render.com

Database runs on elephantSQL.com