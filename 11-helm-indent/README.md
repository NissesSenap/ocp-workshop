# helm intro

Let's reuse what we did in 10.

## Task

- Add readiness and liveness probe to your deployment
- Use helm **nindent** to make it possible for the helm users to decide exactly what readiness probe they want in the template.

I give my helm install **session2** as a name:
`helm install session2 ./mychart`

### Tip

Look at 08 solution if you are unsure how to do the basic health check.

Instead of using `helm install` and `helm delete` between each change you are making to your helm chart.
Use `helm upgrade`

If you want inspiration look create a new helm chart `helm create mychart2` and look how they have done.

Else use the official [helm docs.](https://helm.sh/docs/)

### Verify

Assuming that you used session2 as basename when performing `helm upgrade`.

```bash
oc get pod
# Should give something like:
NAME                       READY   STATUS    RESTARTS   AGE
session2-cc98f9cf5-8gp9s   1/1     Running   0          5m16s
```

oc get pod <pod-name> -o jsonpath="{.spec.containers[0].livenessProbe}"
