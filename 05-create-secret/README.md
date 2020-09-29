# Create secret

Here you can find the official Openshift [docs](https://docs.openshift.com/container-platform/4.5/nodes/pods/nodes-pods-secrets.html) on how to create a secret.

## Secret

oc get secret

## Create the secret

### Create from literal

```oc create secret generic prod-db-secret --from-literal=username=produser --from-literal=password=secretPassw0rd```

### Create with yaml

oc create -f secret.yaml

## Base64

In kubernetes a secret is base64 encoded so it isn't encrypted.

Have a look at the real value in a secret and copy the string under data.username.

oc get secret prod-db-secret -o yaml

or do a one liner

```oc get secret prod-db-secret -o go-template --template='{{.data.username}}'```

### Decode base64

echo cHJvZHVzZXI= |base64 --decode
