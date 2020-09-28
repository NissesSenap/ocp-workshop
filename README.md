# Workshop session 1

This repo goes through a number of basic API:s of kubernetes with some mentions of openshift such as route.
The main reason why I create this repository is that I didn't find a single workshop that contained everything I wanted to go through.

In the repo you will find multiple folders that contain different tasks defined in a README.
It will also contain a solutions folder if everything isn't explained in the README.

In the README you will also find tasks to be done from time to time.
Where you will need to use external resources to solve it.

## Asumption

- Assuming that you are using a decently new OCP like 4.5.
- That you are allways working in your project/namespace

## External resources

oc explain <api>

https://docs.openshift.com/container-platform/4.5/welcome/index.html

https://kubernetes.io/docs/home/

### More workshops

https://learn.openshift.com/

### My cheat sheet

Here you can find my cheat sheet, it contains lots of lots of things that you don't need in this stage of your learning but it's nice to get some insperation some times.

I update it from time to time.

https://github.com/NissesSenap/ocp4GoodToHave/blob/master/oc.md

## Customer specific

If you are going to reuse this repo you probably want to set a few custom specific things.

### Correct uri

find . -type f -name '*.md' -exec sed -i 's/my-domain/my-domain/g' {} \;

### Proxy artifactory

If you are like me and rather ofen is storing your containers in a external artifactory here is a simple sed command to replace to default gcr.io

find . -type f -name '*.yaml' -exec sed -i 's/gcr.io/artifactory.my-domain\/docker-gcr.io/g' {} \;

