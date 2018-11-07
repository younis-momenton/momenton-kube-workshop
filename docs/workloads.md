# Workloads

---

This document describes how a workshop attendee can deploy workloads to the cluster.

---

## Jenkins

[Chart](https://github.com/helm/charts/tree/master/stable/jenkins)

**Notes**

* Replace `<name>` with your name.
* The `digio-values.yaml` must have a correct value for `HostName`.

```console
helm upgrade --install <name>-jenkins \
  --namespace <name> \
  -f charts-values/jenkins/digio-values.yaml \
  --version 0.16.18 \
  stable/jenkins
```

Get the `admin` password with the following command.

```
printf $(kubectl get secret --namespace <name> <name>-jenkins -o jsonpath="{.data.jenkins-admin-password}" | base64 --decode);echo
```


## DinD

**Notes**

* Replace `<name>` with your name.

```console
helm upgrade --install dind \
  --namespace <name> \
  charts/dind/
```