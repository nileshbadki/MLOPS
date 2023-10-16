# Churn Prediction

## Docker Containerization 

Docker containerization is a process that allows you to package an application and its dependencies into a standardized unit called a container
It is possible to build docker images using github actions. Github actions are environment where you can build your container images.
Here I am building a prediction application based on Docker

### containerization process:
1. Install Docker:

Before you can create and run containers, you need to install Docker on your host system. 

2. Write a Dockerfile:

The Dockerfile is a text file that contains instructions for building a Docker image. It specifies the base image, copies application code and dependencies, sets environment variables, and defines how the container should run.

# Use an official Python runtime as the base image
FROM python:3.8

# Set the working directory in the container
WORKDIR /app

# Copy the application code into the container
COPY . /app

# Install application dependencies
RUN pip install -r requirements.txt

# Specify the command to run when the container starts
CMD ["python", "app.py"]


To create a GitHub Actions workflow that builds a Docker image and pushes it to Docker Hub whenever there is a push to the main branch, you can follow these steps. Below is a simplified example of how you can define a GitHub Actions workflow for this purpose:

Create a .github/workflows Directory:

In your GitHub repository, create a .github/workflows directory. This is where you'll store your workflow configuration files.

Create a main.yaml Workflow File:

Inside the workflows directory, create a main.yaml file. This file defines the GitHub Actions workflow. Here's an example main.yaml file:

This workflow does the following:

It triggers on pushes to the main branch.
It runs on the latest version of the Ubuntu environment.
It checks out your code.
It logs in to Docker Hub using your Docker Hub username and password (stored as GitHub secrets).
It builds a Docker image from your repository's code.
It tags the image and pushes it to Docker Hub.
Set Up Secrets:

You need to set up two secrets in your GitHub repository: DOCKER_USERNAME and DOCKER_PASSWORD. These secrets allow GitHub Actions to log in to Docker Hub securely.

DOCKER_USERNAME: Your Docker Hub username.
DOCKER_PASSWORD: Your Docker Hub password or personal access token.
Commit and Push:

Commit the main.yaml file to your repository and push it to the main branch.

Now, when you push changes to the main branch, GitHub Actions will automatically trigger the workflow, build the Docker image, and push it to Docker Hub