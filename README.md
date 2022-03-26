[![patson21](https://circleci.com/gh/patson21/DevOps_Microservices/tree/submission.svg?style=svg)](https://app.circleci.com/pipelines/github/patson21/DevOps_Microservices/?branch=submission)

## Project Overview

This project contains a pre-trained, `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). This project tests your ability to operationalize a Python flask app—in a provided file, `app.py`—that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

---

## Instruction & How to

### Setup the Environment

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
* While you still have your .devops environment activated, you will still need to install:

    Docker ([Instructions for installation](https://docs.docker.com/get-docker/))
    
    Hadolint [Github Repo for installation](https://github.com/hadolint/hadolint))
    
    Kubernetes (Minikube) [Instructions for installation](https://minikube.sigs.k8s.io/docs/start/)

### Building the docker image and run flask app
* cli commands
```bash
docker build --tag=ml_devops .
docker run --rm -p 8000:80 --name flaskapp ml_devops
```

### Test the flask app and make a prediction
* open a separate tab or terminal window
* navigate to the main project directory and call
```bash
./make_prediction.sh
```
* in order to quit the running application type CTRL+C (+enter)

### Possibilities to run `app.py`

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh`
3. Run in Kubernetes (first see Kubernetes steps below):  `./run_kubernetes.sh`

### Kubernetes Steps

* Setup and Configure Docker locally
* Setup and Configure Kubernetes locally
* Create Flask app in Container
* Run via kubectl

---

## Explanation of repository files
* app.py (flask app including the housing price prediction functionality)
* Dockerfile (file to create the docker image that containerizes the flask machine learning microservice)
* requirements.txt (list of required libraries that come as pip packages)
* run_docker.sh (shell script to build docker image and run the machine learning app (app.py) in a containerized environment)
* upload_docker.sh (shell script to tag and push built image to a docker remote repository after authentication)
* make_prediction.sh (shell script to send a pricing predicition request to the containerized service running on the localhost)
* run_kubernetes.sh (shell script to run the containerized application within a kubernetes cluster (needs to be launched in advance), connected to localhost)
* .circleci/config.yml (CI script to lint python and Docker files with a CircleCI Runner)

