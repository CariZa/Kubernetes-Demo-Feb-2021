# Kubernetes-Demo-Feb-2021
The commands I'd like to run through for the demo

Still a work in progress :) not final - many changes to come

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
Demo nth:
----------

Clean it up

    $ minikube stop 

    $ kind delete cluster --name my-kind-cluster

    $ gcloud container clusters delete gcp-manual-demo-cluster --region=europe-west4-a --project $GCP_PROJECT

GitOps (kind of)

    Create delete tag on github
