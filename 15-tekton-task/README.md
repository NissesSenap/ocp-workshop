# tekton task

Lets create and trigger a simple tekton task.

## Task

- Create a taskrun that uses openshift-client defined in task-oc.yaml
- The command that should be used in the task is: `oc get pods`
- Have a look at the [tekton hub](https://hub-preview.tekton.dev/), there are many pre-defined tasks

### Resources

I assume that you have a decently new tekton operator installed in your cluster.

Look at the official [tekton docs](https://tekton.dev/docs/pipelines/taskruns/)

[Upstream tekton catalog](https://github.com/tektoncd/catalog/tree/master/task)

[Tekton hub](https://hub-preview.tekton.dev/)

### Tip

https://tekton.dev/docs/pipelines/taskruns/#specifying-a-pod-template gives a good overview on what a taskrun actually looks like.
But you can remove a bunch of things in it.

You can also create a taskrun from the console.

If you get an issue with running your `oc get pods` command from within the pod you probably need a service account.
Use **deployer** for simplicity, this should not be used in prod.

This is a small example on how a service account can look like in a taskrun.

```yaml
spec:
  serviceAccountName: deployer
```

**NOTE** if you install openshift-pipelines you automatically get a pipeline account with a decent level of access.

### Verify

Assuming that you used the name `oc-taskrun` for your taskrun.

tkn tr ls

tkn tr logs oc-taskrun

## Command

There is multiple ways of getting tekton info.
Since everything is CRD you can simply do `oc get task`

Or you can use the [tekton cli](https://github.com/tektoncd/cli/releases/tag/v0.13.0)

The tekton cli helps out with a number of things and I recommend using it.

### task

oc get task

### tkn

tkn task ls

or

tkn t ls
