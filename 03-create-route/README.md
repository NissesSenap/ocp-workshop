# 03-create-route

So it's time to reach your pod through ingress.

Since we are on OCP we will use a route and this is the first openshift specific API that we are using.

## DNS

Rememeber the default routes created in OCP

<service-name>-<namespace>.apps.cluster-uri

## Create route

oc get route

### cli

oc expose svc my-service

### yaml

oc create -f route.yaml

## Task

Create a https route
