# kubernetes-opnsense-controller-chart

This is a direct fork of travisghansen/kubernetes-pfsense-controller-chart, which is used to deploy the kubernetes-opnsense-controller (also a fork of travisghansen's pfsense controller integration) on k8s clusters using Helm.

## Prerequisites

- A running OPNsense firewall.
- The user must have the necessary permissions to create and manage firewall rules, aliases, and other required resources on the OPNsense firewall.
- The API key and secret for the OPNsense user must be available.

## Installing the Chart

Chart to install `kubernetes-opnsense-controller`

```
helm repo add kubernetes-opnsense-controller https://moellere.github.io/kubernetes-opnsense-controller-chart/
helm repo update
```

To install the chart with the release name `my-release`:

```
helm install my-release kubernetes-opnsense-controller/kubernetes-opnsense-controller
```

## Configuration

The following table lists the configurable parameters of the kubernetes-opnsense-controller chart and their default values.

| Parameter | Description | Default |
| --- | --- | --- |
| `opnsense.url` | The URL of the OPNsense firewall | `http://192.168.1.1` |
| `opnsense.insecure` | Whether to allow insecure connections to the OPNsense firewall | `true` |
| `opnsense.username` | The username for the OPNsense firewall | `admin` |
| `opnsense.password` | The password for the OPNsense firewall | `opnsense` |
| `config` | The configuration for the controller | See `values.yaml` |
| `replicaCount` | The number of replicas for the controller | `1` |
| `image.repository` | The image repository for the controller | `docker.io/moellere/kubernetes-opnsense-controller` |
| `image.pullPolicy` | The image pull policy for the controller | `Always` |
| `image.tag` | The image tag for the controller | `latest` |
| `serviceAccount.create` | Whether to create a service account | `true` |
| `serviceAccount.name` | The name of the service account to use | `""` |
| `rbac.enabled` | Whether to create RBAC resources | `true` |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```
helm install my-release kubernetes-opnsense-controller/kubernetes-opnsense-controller --set opnsense.url=https://my-opnsense.example.com
```

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```
helm install my-release kubernetes-opnsense-controller/kubernetes-opnsense-controller -f values.yaml
```
