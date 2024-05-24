[https://argo-workflows.readthedocs.io/en/latest/quick-start/](https://argo-workflows.readthedocs.io/en/latest/quick-start/)
[Github release](https://github.com/argoproj/argo-workflows)

## First, specify the version you want to install in an environment variable. Modify the command below:
```sh
kubectl create namespace argo 
wget https://github.com/argoproj/argo-workflows/releases/download/v3.5.6/quick-start-minimal.yaml > 0-install-argoworkflow-file.yaml
kubectl apply -n argo -f quick-start-minimal.yaml
kubectl -n argo get po  
kubectl -n argo get deploy argo-server
kubectl -n argo wait deploy --all --for condition=Available --timeout 2m
```

## Edit service to Loadbalancer
https://10.0.0.87:2746/

## Submit an example workflow
```sh
argo submit -n argo --watch https://raw.githubusercontent.com/argoproj/argo-workflows/main/examples/hello-world.yaml
argo list -n argo
argo get -n argo @latest
argo logs -n argo @latest
```

## delete the workflow
```sh
argo list -n argo
argo delete -n argo hello-world-7mglc 
```

## create workflow files
```sh
kubectl -n argo apply -f 1-example-workflow.yaml
kubectl -n argo apply -f 2-example-workflow.yaml
kubectl -n argo apply -f 3-DAG-example-workflow.yaml
```


