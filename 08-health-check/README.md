# Health-check

One of the may reasons to adopt a system like Openshift is the power of auto healing.
If a pod all of the sudden starts to get issues it just gets restarted.

To get this nice feature in your deployment you need to explain to kubernetes when your system is healthy.

Enter Readiness and Liveness

The test container that we are using doesn't have any /health endpoint so we will just go to /

## Task

- Add liveliness probe that uses curl on localhost:8080/

If you are having a http page that you can do there is a pre defined probe for that.
See readiness.yaml, but I want to show the possibilities.

### Tip

oc explain pod.spec.containers.livenessProbe

https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/

### Verify

oc get pod <pod-name> -o jsonpath="{.spec.containers[0].livenessProbe}"

## requests

To view a basic request checkout resources.yaml

oc apply -f readiness.yaml
