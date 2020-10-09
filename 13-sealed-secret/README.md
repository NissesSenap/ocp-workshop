# sealed secret

Now we are starting to talk about rather customer specific solutions.

If you are applying GitOPS and don't have a system like HashiCorp vault you probably want to encrypt your secrets in your git repo.
Sealed secrets is one of the ways of doing this.

## Task

- Create a sealed-secret using kubeseal cli

### Resources

You can find the kubeseal cli [here](https://github.com/bitnami-labs/sealed-secrets/releases)

### Tip

Don't forget to look at sealed-secret.yaml file after generating it.

### Verify

oc get sealedsecret

oc get secret -o yaml

You should see something like

```yaml
ownerReferences:
- apiVersion: bitnami.com/v1alpha1
  controller: true
  kind: SealedSecret
  name: example-secret
```

This means that the the SealedSecret is parent to this secret.
Try to remove the parent and see what happens.

## Command

### kubeseal

You don't need the --controller if you put the sealed secret in the sealed-secret default namespace (can't remember what it is).
But it didn't feel right from a OCP point of view.

kubeseal --controller-name=sealed-secrets --controller-namespace=sealed-secrets -o yaml < example-secret.yaml > sealed-secret.yaml
