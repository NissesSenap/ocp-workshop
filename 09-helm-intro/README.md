# helm intro

Steeling with pride: https://helm.sh/docs/chart_template_guide/getting_started/

Helm is the main templateing solution together with kustomize in the kubernetes space and it's something that I normally use.
So lets do some basic templateing tasks.

## Task

- Add a configmap with Release.Name
- Add a configmap with a values from values file

### Tip

The first task you will find under: https://helm.sh/docs/chart_template_guide/getting_started/
The second step https://helm.sh/docs/chart_template_guide/subcharts_and_globals/

## requests

Checkout the standard configmap.yaml

oc apply -f configmap.yaml

## Commands

helm ls

### Install

helm install random-name path

helm install foo .

### Lint

helm lint

### Upgrade

Install if foo doesn't exist.

helm upgrade --install foo .
