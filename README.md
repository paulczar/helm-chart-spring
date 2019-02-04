# Spring Chart

[Spring](http://spring.io/) is a modern Java framework for developing Cloud Native Applications.

## Chart Details

This chart is designed to be a general purpose chart for running Spring based applications, most simple Spring applications should run with little to no modification of this Chart. For the sake of example this chart is configured to deploy the Spring Petclinic example application, but simply changing the image and tag should be enough to run a different app.

## Installing the Chart

To install the chart with the release name `my-release`:

```bash
$ helm install --name my-release stable/spring
```

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
helm delete --purge my-release
```

The command removes nearly all the Kubernetes components associated with the
chart and deletes the release.

## Configuration

The following table lists the configurable parameters of the drone charts and their default values.

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```bash
helm install --name my-release -f values.yaml stable/spring
```

> **Tip**: You can use the default [values.yaml](values.yaml)

| Parameter | Description | Default |
|-----------|-------------|---------|
| `replicaCount` | The number of replicas | `1` |
| `image.repository`  | location of image to run | `paulczar/petclinic` |
| `image.tag`         | **server** image tag | `2.1.0.BUILD-SNAPSHOT` |
| `image.pullPolicy`  | **server** image pull policy | `IfNotPresent` |
| `serviceAccount.create` | If true, create and use service account | `true` |
| `serviceAccount.name` | If set override the name of the service account |  |
| `rbac.create`  | If true, create and use RBAC resources | `true` |
| `resources` | Resource requests and limits | `{}` |
| `tolerations` | List of node taints to tolerate | `[]` |
| `nodeSelector` | Node labels for pod assignment | `{}` |
| `podAnnotations` | Annotations to apploy to the pod | `{}` |
| `spring.profile` | The spring profile to activate | `nil` |
| `spring.trustKubernetesCertificates` | ensure spring trusts kubernetes certs | `true` |
| `spring.config.type` | type of spring config (currently only supports `file`) | `file` |
| `spring.config.content` | YAML to be placed in `/config/application.yml` | `nil` |
| `spring.config.secretName` | Name of a secret containing `secret.yml:` key to be placed in `/config/secret.yml` | `nil` |
| `containerPort` | the port your application listens on | `8080` |
| `extraEnv` | extra environment variables to pass to your application | `{}` |
| `livenessProbe` | Values to enable livenessProbe suitable for your application | `{}` |
| `readinessProbe` | Values to enable readinessProbe suitable for your application | `{}` |
| `service.enabled` | Enable creating a service | `true` |
| `service.type` | Kubernetes Service type | `ClusterIP` |
| `service.httpPort`| Service HTTP port | `80` |
| `service.nodePort` | Kubernetes http node port | `nil` |
| `service.externalTrafficPolicy` | Enable client source IP preservation | `Cluster` |
| `service.loadBalancerIP` | LoadBalancerIP for the App | `nil` |
| `service.annotations` | Service annotations | `{}` |
| `ingress.enabled` | Enable ingress controller resource | `false` |
| `ingress.annotations` | Ingress annotations | `[]` |
| `ingress.certManager` | Add annotations for cert-manager | `false` |
| `ingress.hosts` | Hostname(s) to your spring app | `[]` |
| `ingress.tls.secretName` | Name of secret holding TLS certs | `nil` |
| `ingress.tls.hosts` | Hostname(s) to your spring app behind TLS | `[]` |
