# helm intro

Let's reuse some of our old resources but building it as a helm template.

Use deployment.yaml and services.yaml as a base when performing the bellow tasks.

## Task

- Create values for cpu & memory for both limits and requests.
  - Order these values in a easy to use way in the values file.
- Use these values in the deployment.yaml
- Use Release.Name instead of hello-world in metadata.name in deployment.yaml
- Set the services ports as values in service.yaml

I give my helm install **session2** as a name:
`helm install session2 ./mychart`

### Tip

If you are unsure look at the solution in 09.

You might hit issues like:

```bash
Error: rendered manifests contain a resource that already exists. Unable to continue with install: existing resource conflict: namespace: workshop, name: my-service, existing_kind: /v1, Kind=Service, new_kind: /v1, Kind=Service
```

This is due to that helm isn't owner of that resource.
Delete the resource that gets the issue or rename the new resource.

### Verify

Assuming that you used session2 as basename when performing `helm install`.

```bash
oc get deployment session2

# Should give
NAME       READY   UP-TO-DATE   AVAILABLE   AGE
session2   1/1     1            1           10m
```

and

```bash
oc get pod
# Should give something like:
NAME                       READY   STATUS    RESTARTS   AGE
session2-cc98f9cf5-8gp9v   1/1     Running   0          5m28s
```

```oc get svc my-service -o jsonpath="{.spec.ports[0].port}"```

Should still return 8080 but hopefully grabbed from values.yaml file.
