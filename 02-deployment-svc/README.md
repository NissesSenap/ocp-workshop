# 02-deployment-svc

## Create deployment

oc create -f deployment.yaml

## Create a service

### Using cli

oc expose deployment hello-world --name=my-service

## using yaml

oc create -f service.yaml
