# Automating Workflow Of CI/CD for Dockerized Flask App Using Github Action

This project demonstrates how to automate the CI/CD workflow for a Dockerized Flask application using GitHub Actions.

## Project Structure

## Files Description

- **app.py**: A simple Flask application that returns "Hello World!" at the root endpoint.
- **test_app.py**: Contains a test case for the Flask application.
- **DockerFile**: Dockerfile to containerize the Flask application.
- **requirements.txt**: Lists the dependencies required for the Flask application.
- **.github/workflows/cicd.yml**: GitHub Actions workflow file to automate the CI/CD process.
- **.gitignore**: Specifies files and directories to be ignored by git.

## Step-by-Step Guide

### 1. Flask Application

The Flask application is defined in `app.py`:

```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def home():
    return "Hello World!"

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
