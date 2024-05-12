gogs-helm-chart
---

This repo contains the source code for a **simple** Helm chart for [gogs](https://gogs.io/).

This repo can be used to assist with the deployment of gogs into a Kubernetes cluster.

> By default, this helm chart uses an SQLite database, but you can supply the connection details of an external 
> DB if required.

## Configuration

The helm chart will create a ConfigMap which contains a gogs `app.ini` used to override the default values of gogs.
Gogs config values that are commonly used (such as the DB connection details) are exposed as templated values in the 
`gogsConfig` section of the [values.yaml](./gogs/values.yaml).

For the values that can be used see: https://github.com/gogs/gogs/blob/main/conf/app.ini

## Viewing generated manifests

Using the chart's default values:

```shell
helm install test-deploy --dry-run .\gogs\ > test.yaml
```

With a custom `my-values.yaml` file:

```shell
helm install test-deploy --dry-run -f .\my-values.yaml .\gogs\ > test.yaml
```