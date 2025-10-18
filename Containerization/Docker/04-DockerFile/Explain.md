# Explain

## What is Docker file

A **Docker file** is basically a recipe that tells Docker how to build your image.

- You write instructions (steps) like “start from this base image,” “install this software,” “copy my files,” etc.

## Why we use Docker file

- **Reproducibility** → You (or anyone) can rebuild the exact same environment any time.
- **Automation** → No more manually installing packages inside containers.
- **Portability** → You can run the same image anywhere Docker runs.

## Notes about Docker file

- Docker file must has name in dir. (**Dockerfile**)
- The dir. which has docker file is in docker host and called : **build-context**
- Run commands use intermediate containers to execute commands then delete it
- Each instruction = layer , if u execute it separately → it will be in (R-W) layer
- Docker file executes instructions line by line
- If any line causes an error → docker file stops
- While pushing to Docker hub → Docker hub compares the layers and push the difference not from scratch like GitHub

## .dockerignore

- Used to ignore some files i don’t need to use in docker file
- Benefits
    - **Makes build faster**
    - **Keeps image smaller**
    - **Avoids exposing secrets**
- We make .dockerignore file then write which files we don’t need to use