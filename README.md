# workshop02

## Required
* A functional OCP environment that can run builds
* git and oc clients

## Clone the workshop02 repo
```sh
# clone the repo
git clone https://github.com/rhocpws/workshop02.git

# change to the repo directory
cd workshop02
```

## Deploy the project
```sh
# login to your ocp environemt
oc login https://[YOUR_OCP_SERVER]:6443

# create the project
oc create -f .
```

## Start the build
```sh
# set the project
oc project workshop02

# check the build config name
oc get bc

# run the build
oc start-build workshop02

# tail the build logs
oc logs -f `oc get pods -n workshop02 | grep build | awk '{print $1}'`

# the build is complete when it says "Push successful" ctrl+c to exit
```

## Check the pod and connect to the route
```sh
# check that the pod is running
oc get pods -n workshop02

# get the route, copy/paste it to your web browser
oc get routes -n workshop02
``
