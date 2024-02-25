# Java Demo App CICD Project

- This is a simple spring boot application in which Continuous Integration is done using the Jenkins and Continuous Deployment is done on Kubernetes using Agro CD.
- The spring boot application when deployed displays a simple text message to users.

## Continuous Integration  
- Installed jenkins on the VM and configured to get the code from the github repository.
- The Jenkinsfile CI file containes three major stages:
  - #### Build and Test stage:
    - In this stage the we build the project and create a JAR file
  - #### Build and Push Docker Image stage:
    - In this stage we build the docker image and push it to the docker hub with the tag as the jenkins build number.
  - #### Update Deployment File
    - In this stage we replace the existing image version in the deployment yaml file with the new image version using shell script.
    - After that we will commit the deployment file to the GIt repository.

## Continuous Deployment
- Installed minikube and Argo CD on the VM provided.
- Argo CD is accessible by the below command
```kubectl port-forward --address 157.245.111.40 svc/argocd-server -n argocd 8082:44```
- Configures ArgoCD to the GIT repository path of Kuberenets manifest files.
- As Argo CD watches for any changes in the Repository path and once the new vesrion of the image is deployed using the shell script it deploys the same change on the Kubernetes cluster.
- Once the new version of image got deployed on the Kubernetes cluster we can see the changes in the service 

