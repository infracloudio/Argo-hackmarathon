# Argo-hackmarathon
---------------------------------------------------
## Project Details
Consider you have a microservice application running on some cloud platform, whenever developer makes any changes in code the respective microservice should be updated.

Sock Shop demo application https://github.com/microservices-demo/microservices-demo

## How it works?
1. Consider sock shop demo app is deployed on cloud platform.
2. Developer pushed new change to git
3. Argo workflow

         i. Pull latest git changes
         ii.  Build new docker image 
         iii. Push the docker images to dockerhub
         iv. Update the deployment


## Install Argo
Execute following commands
```
curl -sSL -o argo https://github.com/argoproj/argo/releases/download/v2.2.1/argo-linux-amd64
sudo cp argo /usr/local/bin/.
sudo chmod +x /usr/local/bin/argo
kubectl create ns argo
kubectl create clusterrolebinding cluster-admin-binding --clusterrole=cluster-admin --user=<emailid>
kubectl apply -n argo -f https://raw.githubusercontent.com/argoproj/argo/v2.2.1/manifests/install.yaml
kubectl create rolebinding default-admin --clusterrole=admin --serviceaccount=default:default
```

## Access the Argo UI
```
kubectl -n argo port-forward deployment/argo-ui 8001:8001
```
Then visit: http://127.0.0.1:8001 

## Execute Argo Workflow
```
argo submit argo-workflow.yaml
```

## Next steps
1. Tryout Argo CI



