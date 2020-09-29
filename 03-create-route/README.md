# 03-create-route

So it's time to reach your pod through ingress.

Since we are on OCP we will use a route and this is the first openshift specific API that we are using.

## Task

Create a https route

## DNS

Rememeber the default routes created in OCP

<service-name>-<namespace>.apps.cluster-uri

## Create route

oc get route

### cli

oc expose svc my-service

### yaml

oc create -f route.yaml

## verify route

To view the ingress perform

oc get route my-service

### one liner

oc get route my-service -o go-template --template='{{.spec.host}}'

And add a curl on that.

curl $(oc get route my-service -o go-template --template='{{.spec.host}}')'
