# Atomating Workflow CI/CD

This repository demonstrates how to automate Continuous Integration and Continuous Deployment (CI/CD) workflows using **GitHub Actions**. It includes a complete pipeline for building, testing, and deploying a Dockerized Flask application.

## Features

- **CI/CD Pipeline**: Automates building, testing, and deploying a Dockerized Flask application.
- **GitHub Actions Integration**: Uses workflows for:
  - Building Docker images.
  - Running automated tests.
  - Pushing images to Docker Hub.
- **Secure Credentials**: Implements GitHub Secrets to manage Docker Hub login securely.

## Creación de Secrets en mi repositorio

![Creación de Secrets - Imagen 1](docs/imagen1.png)
![Creación de Secrets - Imagen 2](docs/imagen2.png)
![Creación de Secrets - Imagen 3](docs/imagen3.png)

## Creación de Tokens en DockerHub

![Creación de Tokens - Imagen 1](docs/imagen4.png)
![Creación de Tokens - Imagen 2](docs/imagen5.png)
![Creación de Tokens - Imagen 3](docs/imagen6.png)
![Creación de Tokens - Imagen 4](docs/imagen7.png)


## Estructura del proyecto

```
Atomating_worflow_CI_CD/ 
|
├── .github/            # GitHub Actions workflow configuration
|   ├── workflows/
|       ├── cicd.yml
├── venv
├── .gitignore
├── app.py              # Flask application code
├── Dockerfile          # Dockerfile for the application
├── test_app.py  
├── requirements.txt    
├── README.md           # Project documentation    
└── ...
```

## GitHub Actions Workflow

The CI/CD pipeline is defined in `.github/workflows/ci_cd.yaml` and includes the following jobs:

### 1. **Build the Docker Image**

Builds a Docker image from the `Dockerfile` and tags it with a timestamp for unique identification.

### 2. **Run Automated Tests**

Runs `pytest` to ensure the Flask application behaves as expected.

### 3. **Build and Push Docker Image**

Logs into Docker Hub using GitHub Secrets and pushes the Docker image to your Docker Hub repository.

### Example Workflow Steps

```yaml
jobs:
  build-and-publish:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout code
      uses: actions/checkout@v3

    - name: Set up Docker Buildx
      uses: docker/setup-buildx-action@v2

    - name: Login to DockerHub
      uses: docker/login-action@v2
      with:
        username: ${{ secrets.DOCKER_USERNAME }}
        password: ${{ secrets.DOCKER_PASSWORD }}

    - name: Build and push Docker image
      uses: docker/build-push-action@v4
      with:
        context: .
        file: ./Dockerfile
        push: true
        tags: ${{ secrets.DOCKER_USERNAME }}/flasktest-app:latest
```

# Prerequisites
**Docker Installed:** Ensure Docker is installed and running locally.
**GitHub Secrets:**
**DOCKER_USERNAME:** Your Docker Hub username.
**DOCKER_PASSWORD:** A Docker Hub Personal Access Token (PAT).

## How to Run Locally

Clone the repository:

```
git clone <https://github.com/LeoR22/Atomating_worflow_CI_CD.git>
cd Atomating_worflow_CI_CD
```

## Build and run the Docker container

```
docker build -t flask-app .
```

```
docker run -p 5000:5000 flask-app
```

## Open your browser and navigate to <http://localhost:5000>
Open your browser and navigate to <http://localhost:5000>.

## Troubleshooting
GitHub Actions Login Error: Ensure DOCKER_USERNAME and DOCKER_PASSWORD are set correctly in GitHub Secrets.
Test Failures: Run pytest locally to debug test issues.

## Resources
GitHub Actions Documentation: <https://docs.github.com/es/actions>
Docker Hub: <https://hub.docker.com/>


## Contribuciones

¡Las contribuciones son bienvenidas! Por favor, crea un fork del repositorio, realiza tus cambios, y abre un pull request.

## Licencia

Este proyecto está bajo la Licencia MIT. Consulta el archivo `LICENSE` para más detalles.

## Contacto

Leandro Rivera: <leo.232rivera@gmail.com>

### ¡Feliz Codificación! 🚀

Si encuentras útil este proyecto, ¡dale una ⭐ en GitHub! 😊
