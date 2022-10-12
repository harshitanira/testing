Before installing minikube, make sure that your system meets the system requirements and you have a working Container or Virtual Machine manager such as Docker, VirtualBox, etc.

To install and initiate minikube, follow the steps given here: https://minikube.sigs.k8s.io/docs/start/

To run a CI pipeline on minikube, you first need to download Tekton CLI on your system. Follow through the steps given in https://tekton.dev/docs/cli/

Now, you need to install tekton pipelines on your minikube cluster. Do:
- minikube start
- kubectl apply --filename https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml

Now create a namespace as defined in the values.yml file. All the resources used in the pipeline will reside here.
- kubectl create namespace <namespace-name>

Install the following tasks in the namespace that you created:
  1. Maven
     - kubectl apply -f https://api.hub.tekton.dev/v1/resource/tekton/task/maven/0.2/raw
     or 
     - tkn hub install task maven -n <namespace-name>

  2. Kaniko
     - kubectl apply -f https://api.hub.tekton.dev/v1/resource/tekton/task/kaniko/0.6/raw
     or
     - tkn hub install task kaniko -n <namespace-name>

Install helm on your system, https://helm.sh/
Provide the values in values.yaml
Install the pipeline via helm# testing
