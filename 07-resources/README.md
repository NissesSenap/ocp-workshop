# Resources

Great now we can create a deployment that we can configure with secrets and configmaps.
But one of the nice things with containers is that it should use small amounts of resources, lets make sure it actually does that.

You should never go to production without configuring resources.
In openshift you can easily apply default resources for pods and normally a platform team sets the values very low to enforce the developers to set custom ones and at the same utilize as small cluster resources as possible.

## Task

- Add limits resource to 128Mi (memory) and 100m (CPU)

### Tip

oc explain pod.spec.containers.resources

### Verify

oc get pod <pod-name> -o jsonpath="{.spec.containers[0].resources}"

## requests

To view a basic request checkout resources.yaml

oc apply -f resources.yaml
