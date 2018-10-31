# Netbox Helm chart

This directory contains a Kubernetes chart to deploy a Netbox application
container.

## Prerequisites Details

* Kubernetes 1.6+
* A database service installed (MySQL, PostgreSQL) and configured with a user with write/alter schema access to a `netbox` database

## Chart Details

This chart will do the following:

* Implement a Netbox deployment

## Installing the Chart

To install the chart, use the following:

```console
$ helm repo add incubator http://storage.googleapis.com/kubernetes-charts-incubator
$ helm install incubator/netbox
```

## Configuration

The following tables lists the configurable parameters of the vault chart and their default values.

|       Parameter         |           Description               |                         Default                     |
|-------------------------|-------------------------------------|-----------------------------------------------------|
| `image.repository`      | Docker image to use for netbox      | `pitkley/netbox`                                    |
| `image.tag`             | Docker image tag for netbox         | `develop`                                           |
| `netbox.dbhost`         | Database host for netbox            | ``                                                  |
| `netbox.dbuser`         | Database user for netbox            | ``                                                  |
| `netbox.dbpass`         | Database password for netbox        | ``                                                  |
| `netbox.secretkey`      | Django secret key to use for netbox | ``                                                  |
| `netbox.allowedhosts`   | Django allowed hosts for netbox     | ``                                                  |
| `netbox.loginrequired`  | Django login enforcement            | `False`                                             |
| `replicaCount`          | k8s replicas                        | `1`                                                 |
| `resources.limits.cpu`  | Container requested CPU             | `nil`                                               |
| `resources.limits.memory` | Container requested memory        | `nil`                                               |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install` or by modifying `values.yaml` and replacing values as necessary.

If you wish to use `kube-lego` to automatically request a TLS certificate from LetsEncrypt for your `Ingress` rule, uncomment the `kubernetes.io/tls-acme` annotation and `tls` section in `values.yaml`, and update the `tls.secretName` and `tls.hosts` to match your environment.
