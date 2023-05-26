# Usual setup

```bash
python -m venv .venv

source .venv/bin/activate

pip install flask
```

# Flask main stuff

Create "app.py"

```python
from flask import Flask, request

app = Flask(__name__)
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
n

```bash
docker run -p 8000:5000 <image_name>

Example:
docker run -p 8000:5000 flask-smorest-api
```

## Reload app that is running in docker image

-w -> docker folder

-v -> volume (where to find the code)

```bash
docker run -p 8000:5000 -w /app -v "${pwd}:/app" <image_name>

Example:
docker run -p 8000:5000 -w /app -v "$(pwd):/app" flask-smorest-api
```

# API

Checkout the api in
`http://localhost:8000/swagger-ui`
