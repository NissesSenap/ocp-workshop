# bind-secret-to-pod

While it's great to have a secret or a configmap they don't do allot without being used by something.

## Task

- Bind the secret to the pod deployment as a environment called SECRET_PASSWORD
- Bind the configmap to the pod deployment as a file under /config on the pod

### Tip

#### secret

oc explain pod.spec.containers.env

https://kubernetes.io/docs/tasks/inject-data-application/distribute-credentials-secure/

#### configmap

oc explain pod.spec.volumes

oc explain pod.spec.containers.volumeMounts

### Verify

Here is a "simple" one liner to get the first pod name from a label.
Currently more to write then just do a `oc get pod` but if you are performing small changes and do a bunch of deployments it can be really nice.

oc get pod -l app.kubernetes.io/name=load-balancer-example -o jsonpath="{.items[0].metadata.name}"

#### exec

oc exec -i -t <pod-name> -- /bin/sh -c 'echo $SECRET_PASSWORD'

oc exec -i -t <pod-name> -- /bin/sh -c 'cat /config/bootstrap.properties'

#### rsh

oc rsh <pod-name>
