# Exploring DevOps :  Package and Deploy the application  to kubernetes using CI/CD Pipeline

# Introduction

TechTrends is an online website used as a news sharing platform, that enables consumers to access the latest news within the cloud-native ecosystem.  The application is  packaged  with the help of Docker. Github Actions are used to enable continuous integration, thus automating the build and pushing  the docker image to dockerhub. Kubernetes cluster is provisioned using K3s in a vagrant box where the application is deployed. Kubernetes Manifest template is made using Helm Charts and input configuration files for Staging and prod environment are made. ArgoCD is used to enable Continuous Delivery on each deployment at Staging/Prod Environment. 


### Getting Started
1. Clone this repository.
2. Install the dependencies.
3. Setup the Vagrant environment.
4. Package and Deploy the application of your choice.
5. Update this README to reflect how someone would use your code.


### Dependencies
3. Install [Python](https://www.python.org/downloads/)
4. Install [Git](https://git-scm.com/downloads)
5. Install [Docker](https://docs.docker.com/get-docker/)
6. Install [Vagrant](https://www.vagrantup.com/downloads)
7. Install [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
8. Install [ArgoCD](https://argoproj.github.io/argo-cd/getting_started/#1-install-argo-cd)


### Health End Points

The project has /healthz endpoint exposed at [app.py](https://github.com/arunprakashpj/TechTrends/blob/main/techtrends/app.py) file

The project has /metrics endpoint exposed at [app.py](https://github.com/arunprakashpj/TechTrends/blob/main/techtrends/app.py) file

The Logs have been enabled for the project.


### Instructions

1. Package the application using docker
    - Create a dockerfile to package the application. Keep the application of your choice in the project directory. Here I have an application called Tech Trends.
    - Build the docker image. You can check the comamnds to build [here](https://github.com/arunprakashpj/TechTrends/blob/main/docker_commands) 
    - Test the docker image locally. Access the application on http://127.0.0.1:7111 . 

2. Continuous Integration with Github Actions
    - Aim of this step is to automate the packaging of the application using [Github Actions](https://github.com/marketplace/actions/build-and-push-docker-images)
    - Github Actions help us to build, tag and push the docker image of the application to dockerhub
    - If not present, create .github/workflows directory. 
    - To automate the login into Docker Hub, the github actions use [Github Tokens](https://www.docker.com/blog/docker-hub-new-personal-access-tokens/) and [Github Encrypted Secrets](https://docs.github.com/en/actions/reference/encrypted-secrets)
    - Create and verify if the github actions execute on every new commit, thus pushing the latest docker image to the docker hub.
  
  3. Deploy a Kubernates Cluster using K3s
     - Aim of this step is to create a declarative kubernetes manifest and release the application to the sandbox environment
     - Use Vagrant environment and create kubernetes cluster with [k3s](https://k3s.io/). Check attached [vagrant file](https://github.com/arunprakashpj/TechTrends/blob/main/Vagrantfile) for reference
     - To create a vagrant box, navigate to this [location](https://github.com/arunprakashpj/TechTrends/blob/main/Vagrantfile)  where vagrantfile is placed.
     - Use the command ``vagrant up`` , then ``vagrant ssh``
     - You can find the kubernetes declartive manifests [here](https://github.com/arunprakashpj/TechTrends/tree/main/kubernetes).
     - Use the command ``kubectl apply -f yaml_file_name`` to deploy the application in k3s cluster.
  
  4. Helm Charts Templating
     - The aim of this step is to parameterize the kubernetes manifests.
     - You can find the helm charts  [here](https://github.com/arunprakashpj/TechTrends/tree/main/helm).
     - The input values are built for [staging](https://github.com/arunprakashpj/TechTrends/tree/main/helm) and [production](https://github.com/arunprakashpj/TechTrends/tree/main/helm) environment seperately.
   
   5. Continuous Delivery using ArgoCD
       - The aim of this step is to automatically deploy the application using ArgoCD, thus easy release to staging and production environment using the helm chart templates
       - Nodeport Service Yaml files can be found [here](https://github.com/arunprakashpj/TechTrends/tree/main/argocd)
       - Access the argoCD UI at https://192.168.50.4 : 300008 or http://192.168.50.4:30007
       - Login credentials can be retrieved using the steps [here](https://argoproj.github.io/argo-cd/getting_started/#4-login-using-the-cli)
       - Whenever you made a new commit, the application will be packed into docker image and gets deployed.
    
  ###  Visualization of the entire process
  
  ## Fig 1 : Docker Image  
  ![Screenshot](https://github.com/arunprakashpj/TechTrends/blob/main/screenshots/docker-run-local.PNG)
 
  ## Fig 2 : CI Github Actions
  ![Screenshot](https://github.com/arunprakashpj/TechTrends/blob/main/screenshots/ci-github-actions.PNG)
  
  ## Fig 3 : CI DockerHub
  ![Screenshot](https://github.com/arunprakashpj/TechTrends/blob/main/screenshots/ci-dockerhub.PNG)
  
  ## Fig 4 : Kubernetes Manifests
  ![Screenshot](https://github.com/arunprakashpj/TechTrends/blob/main/screenshots/kubernetes-declarative-manifests.PNG)
  
  ## Fig 5 : ArgoCD -Staging Environment
  ![Screenshot](https://github.com/arunprakashpj/TechTrends/blob/main/screenshots/argocd-techtrends-stag.PNG)
  
  ## Fig 6 : ArgoCD - Prod Environment
  ![Screenshot](https://github.com/arunprakashpj/TechTrends/blob/main/screenshots/argocd-techtrends-prod.PNG)
  
  
## Demo 

[![Demo](https://github.com/arunprakashpj/Deploying-CICD-Pipeline-in-Azure/blob/main/Screenshots/clickhere.png)](https://youtu.be/krERbEe88GA)
