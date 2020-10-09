# solution

I can't pre-generate a solution since it's unique per cluster, namespace and secret name.

Just do:

kubeseal --controller-name=sealed-secrets --controller-namespace=sealed-secrets -o yaml < example-secret.yaml > sealed-secret.yaml

And hopefully it should work :)
