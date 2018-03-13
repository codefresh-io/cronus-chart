# Cronus

Cronus is a Codefresh Cron Timer **trigger event provider** service.

## TL;DR

```sh
helm install codefresh/cronus
```

## Introduction

This chart bootstraps a [Cronus](https://github.com/codefresh-io/cronus) deployment on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Prerequisites

- Kubernetes 1.8+ with Beta APIs enabled
- Codefresh Helm Release
- Codefresh Hermes Service

## Installing the Chart

To install the chart with the release name `my-release`:

```sh
helm install --name my-release --namespace codefresh codefresh/cronus
```

The command deploys Cronus on the Kubernetes cluster in the `codefresh` namespace with default configuration. The [configuration](#configuration) section lists the parameters that can be configured during installation.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```sh
helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following tables lists the configurable parameters of the Hermes chart and their default values.

| Parameter              | Description                                                      | Default                      |
| ---------------------- | ---------------------------------------------------------------- | ---------------------------- |
| `image.repository`     | Hermes image                                                     | `codefresh/cronus`           |
| `image.tag`            | Hermes image tag                                                 | `0.1`                        |
| `image.PullPolicy`     | Image pull policy                                                | `IfNotPresent`               |
| `service.name`         | Kubernetes Service name                                          | `cronus`                     |
| `service.type`         | Kubernetes Service type                                          | `ClusterIP`                  |
| `service.externalPort` | Service external port                                            | `80`                         |
| `service.externalPort` | Service internal port                                            | `8080`                       |
| `logLevel`             | Log level: `debug`, `info`, `warning`, `error`, `fatal`, `panic` | `info`                       |
| `event.type`           | Trigger Event type (do not change)                               | `cron`                       |
| `event.kind`           | Trigger Event kind (do not change)                               | `codefresh`                  |
| `hermesService`        | Hermes Service name                                              | `{{ .Release.Name }}-hermes` |
| `store.size`           | Volume size for embedded database (BoltDB)                       | `1Gi`                        |