# Simple helm chart to demonstrate missing newlines from imported file

There is a strange issue with [Helm](https://github.com/helm/charts) eating away newlines when the
file is being imported into variable and then used in `volumes` to be stored as a file on container
being deployed.

Try:
```
$ # install/configure kubernetus cluster, for example minikube
$ git clone git@github.com:AndrewLvov/test-newlines.git
$ helm install --debug --name test-newlines ./test-newlines  --set-file configFile=test-newlines/test-newlines.ini
$ kubectl edit configmaps test-newlines-vars 
```

You will see that the configmap differs frome the file imported (test-newlines.ini)
Compare to `test-newlines.conf` which has been defined inline in comfigmap.yaml
