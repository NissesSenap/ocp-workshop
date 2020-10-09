# solution

Apply the yaml files and create the route.
I have removed the NS definitions from the example.

```bash
oc apply -f example-app.yaml
oc apply -f servicemonitor.yaml
oc expose svc prometheus-example-app
```
