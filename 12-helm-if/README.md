# helm intro

Let's reuse what we did in 11 and in 03.

## Task

- If enabled create a http route that talks to our service.
- Unless autoscaling.enabled is set, configure replicas to 2
  - Use hpa.yaml as base, you will need to update it.
  - Do not create the HPA if it's set to false

I give my helm install **session2** as a name:
`helm install session2 ./mychart`

### Tip

https://helm.sh/docs/chart_template_guide/control_structures/#ifelse

### Verify

Assuming that you used session2 as basename when performing `helm upgrade`.

```bash
oc get pod
# Should give something like:
NAME                       READY   STATUS    RESTARTS   AGE
session2-5846f47559-mm8l8   1/1     Running   0          32m
session2-5846f47559-svq2j   1/1     Running   0          27s

```

Try setting autoscaling.enabled.true, what happens?
You should be able to see a hpa `oc get hpa`

#### Load test your app

While having HPA enabled let's put some load on it.

Assuming that you created a http route, else change MYROUTE to https

```bash
# Grab the uri of your route
export MYROUTE=http://$(oc get route my-service -o go-template --template='{{.spec.host}}')
# Lets create some load
for ((i=1;i<=10000;i++)); do curl -v $MYROUTE; done

# Or start another terminal a do some while instead :)
# Remember you have to do the export in both terminals
while true; do curl -q $MYROUTE; done

```

It can take a few *minutes* to get any good output from the hpa. It might look something like in this in the beginning:

```bash
oc get hpa
NAME        REFERENCE              TARGETS        MINPODS   MAXPODS   REPLICAS   AGE
session2   Deployment/something   <unknown>/5%   1         3         0          3s
```

In another terminal `oc get pods -w`

Hopefully you should see the number of pods increasing.

## Command

### HPA

After doing the task you should see a hpa.

oc get hpa
