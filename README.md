[![CircleCI](https://dl.circleci.com/status-badge/img/gh/hungntong/project-ml-microservice/tree/main.svg?style=svg)](https://dl.circleci.com/status-badge/redirect/gh/hungntong/project-ml-microservice/tree/main)
## Summary
In this project we containerized a simple machine learning app that make prediction of housing market using Docker. 
We further enhanced it by adding logging, and then create a cluster and deploy the app through Kubernetes.
Lastly, we added autochecking using github and CircleCI.

## How to Run Python Scripts
To run the app.py. You'll need to set up a virtual environment, install the required tools, and then run app.py. 

1. python3 -m virtualenv ~/.devops
2. source .devops/bin/activate
3. make install
4. python3 app.py
5. ./make_prediction

To run in docker locally:
1. Make sure docker is install. Follow the link for installation instructions https://docs.docker.com/engine/install.
2. docker --version
3. docker build --tag=<name> .
3. docker image ls
4. docker run -p 8000:80 <name>
5. ./make_prediction.sh

To run container in Kubernetes locally:
1. curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
2. sudo install minikube-linux-amd64 /usr/local/bin/minikube
3. minikube start
4. kubectl config view
5. kubectl get pods
6. kubectl run <name> --image=<path> --port=80
7. kubectl port-forward <name> 8000:80
8. ./make_prediction.sh

## Explanation of Files
* .circleci/config.yml - Contains circleCI build instructions
* app.py - Python code to build the web app
* Dockerfile - contains instructions to build a docker image
* make_prediction.sh - calls /predict with the specified information
* Makefile - contains instructions on how to set up the environment and lint tested
* README.md - project's documentation
* requirements.txt - contains tools that are required to run the app
* run_docker.sh - script to build and run the docker image
* run_kubernetes.sh - script to create the cluster and deploy docker image
* uploads_docker.sh - upload Docker image to Docker Hub

## Project Overview

In this project, you will apply the skills you have acquired in this course to operationalize a Machine Learning Microservice API. 

You are given a pre-trained, `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). This project tests your ability to operationalize a Python flask app???in a provided file, `app.py`???that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

### Project Tasks

Your project goal is to operationalize this working, machine learning microservice using [kubernetes](https://kubernetes.io/), which is an open-source system for automating the management of containerized applications. In this project you will:
* Test your project code using linting
* Complete a Dockerfile to containerize this application
* Deploy your containerized application using Docker and make a prediction
* Improve the log statements in the source code for this application
* Configure Kubernetes and create a Kubernetes cluster
* Deploy a container using Kubernetes and make a prediction
* Upload a complete Github repo with CircleCI to indicate that your code has been tested

You can find a detailed [project rubric, here](https://review.udacity.com/#!/rubrics/2576/view).

**The final implementation of the project will showcase your abilities to operationalize production microservices.**

---

## Setup the Environment

* Create a virtualenv with Python 3.7 and activate it. Refer to this link for help on specifying the Python version in the virtualenv. 
```bash
python3 -m pip install --user virtualenv
# You should have Python 3.7 available in your host. 
# Check the Python path using `which python3`
# Use a command similar to this one:
python3 -m virtualenv --python=<path-to-Python3.7> .devops
source .devops/bin/activate
```
* Run `make install` to install the necessary dependencies

### Running `app.py`

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh`
3. Run in Kubernetes:  `./run_kubernetes.sh`

### Kubernetes Steps

* Setup and Configure Docker locally
* Setup and Configure Kubernetes locally
* Create Flask app in Container
* Run via kubectl
