# Workloads

---

This document describes how a workshop attendee can deploy workloads to the cluster.

---

## Helm

```console
helm init
```


## Jenkins

[Chart](https://github.com/helm/charts/tree/master/stable/jenkins)

```console
helm upgrade --install jenkins \
  --namespace jobs \
  -f charts-values/jenkins/values.yaml \
  --version 0.16.18 \
  stable/jenkins
```

Get the `admin` password with the following command.

```console
printf $(kubectl get secret --namespace jobs jenkins -o jsonpath="{.data.jenkins-admin-password}" | base64 --decode);echo
```


## DinD

```console
helm upgrade --install dind \
  --namespace jobs \
  charts/dind/
```