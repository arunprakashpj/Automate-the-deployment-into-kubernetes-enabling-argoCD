# Exploring DevOps :  Package and Deploy the website to kubernetes using CI/CD Pipeline

# Introduction

TechTrends is an online website used as a news sharing platform, that enables consumers to access the latest news within the cloud-native ecosystem.  The application is  packaged  with the help of Docker. Github Actions are used to enable continuous integration, thus automating the build and pushing  the docker image to dockerhub. Kubernetes cluster is provisioned using K3s in a vagrant box where the application is deployed. Kubernetes Manifest template is made using Helm Charts and input configuration files for Staging and prod environment are made. ArgoCD is used to enable Continuoud Delivery on each deployment at Staging/Prod Environment 


### Getting Started
1. Clone this repository

2. Install [Python](https://www.python.org/downloads/), [Git](https://git-scm.com/downloads), [Docker](https://docs.docker.com/get-docker/), [Vagrant](https://www.vagrantup.com/downloads), [VirtualBox](https://www.virtualbox.org/wiki/Downloads)

3. Update this README to reflect how someone would use your code.
Experimenting with Github Actions!


### Health End Points

The project has /healthz endpoint exposed at app.py file

The project has /metrics endpoint exposed at app.py file

The Logs have been enabled for the project

