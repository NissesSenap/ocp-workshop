# create configmap

Here you can find the official Openshift [docs](https://docs.openshift.com/container-platform/4.5/builds/builds-configmaps.html) on how to create a configmap.

## configmap

oc get configmap

## Create the CM

### Create from file

oc create configmap cm-bootstrap --from-file=bootstrap.properties

### Create with yaml

oc create -f cm.yaml
