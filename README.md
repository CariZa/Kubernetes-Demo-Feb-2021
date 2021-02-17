# Kubernetes-Demo-Feb-2021
The commands I'd like to run through for the demo

Still a work in progress :) not final - many changes to come

Pre demo checks:

    $ kubectx

If there's still any kind cluster - remove 

    $ kind delete cluster --name my-kind-cluster

Check if minikube is running:

    $ minikube status

Check it there's any running gcp kubernetes clusters

    $ gcloud container clusters list

----------
## Demo 1:
----------

Create some clusters:

    $ export KUBECONFIG=$HOME/.kube/kubeconfig

Local clusters:

    $ minikube start

    $ kind create cluster --name my-kind-cluster

    $ kubectl cluster-info --context kind-my-kind-cluster

GCP:

    $ export GCP_PROJECT=xxx

    $ gcloud config set project $GCP_PROJECT

    $ gcloud container clusters create  gcp-manual-demo-cluster \
    --region=europe-west4-a \
    --num-nodes=2

    $ gcloud container clusters get-credentials gcp-manual-demo-cluster --region=europe-west4-a --project $GCP_PROJECT



----------
## Demo 2:
----------

Demo GitOps (kinda)

Git Repo

https://github.com/CariZa/Kubernetes-Demo-Jan-2021

CRD

Deployments
Pods
Service 
Namespaces


----------
Demo 3:
----------

Wordpress the hard way 

(aka not with helm)

    Docker -> docker-compose -> Kubernetes

Show a docker compose file
- the layers

Deconstruct the docker compose into a kubernetes flow.

Run docker-compose 

    $ docker-compose up -d

Visit the running services:

Wordpress UI
http://localhost:8000

PHPMyAdmin
http://localhost:8080



Stop docker-compose:

    $ docker-compose down

Select a kubernetes cluster context (requires the kubectx cli tool):

    $ kubectx 


Apply the yaml files to a kubernetes cluster:

    $ kubectl apply -f k8s/wordpress/namespace.yaml -f k8s/wordpress/ -n wordpress

Switch to namespace (requires the kns cli tool):

    $ kns wordpress


----------
Demo nth:
----------

Clean it up

    $ minikube stop 

    $ kind delete cluster --name my-kind-cluster

    $ gcloud container clusters delete gcp-manual-demo-cluster --region=europe-west4-a --project $GCP_PROJECT

GitOps (kind of)

    Create delete tag on github
