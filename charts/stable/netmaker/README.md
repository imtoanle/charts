# netmaker

![Version: 0.2.0](https://img.shields.io/badge/Version-0.2.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.14.5](https://img.shields.io/badge/AppVersion-0.14.5-informational?style=flat-square)

A Helm chart to run HA Netmaker on Kubernetes

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose)**

## Requirements

## Dependencies

| Repository | Name | Version |
|------------|------|---------|
| https://charts.bitnami.com/bitnami | postgresql-ha | 7.11.0 |

## TL;DR

```console
helm repo add k8s-at-home https://k8s-at-home.com/charts/
helm repo update
helm install netmaker k8s-at-home/netmaker
```

## Installing the Chart

To install the chart with the release name `netmaker`

```console
helm install netmaker k8s-at-home/netmaker
```

## Uninstalling the Chart

To uninstall the `netmaker` deployment

```console
helm uninstall netmaker
```

The command removes all the Kubernetes components associated with the chart **including persistent volumes** and deletes the release.

## Configuration

Read through the [values.yaml](./values.yaml) file. It has several commented out suggested values.
Other values may be used from the [values.yaml](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common/values.yaml) from the [common library](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common).

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

```console
helm install netmaker \
  --set env.TZ="America/New York" \
    k8s-at-home/netmaker
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart.

```console
helm install netmaker k8s-at-home/netmaker -f values.yaml
```

## Custom configuration

N/A

## Values

**Important**: When deploying an application Helm chart you can add more values from our common library chart [here](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common)

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| dns.enabled | bool | `false` | whether or not to deploy coredns |
| dns.storageSize | string | `"128Mi"` |  |
| fullnameOverride | string | `""` | override the full name for netmaker objects  |
| image.pullPolicy | string | `"Always"` | Pull Policy for images |
| image.repository | string | `"gravitl/netmaker"` | The image repo to pull Netmaker image from  |
| image.tag | string | `"v0.14.5"` | Override the image tag to pull  |
| ingress.annotations.base."kubernetes.io/ingress.allow-http" | string | `"false"` | annotation to generate ACME certs if available |
| ingress.annotations.nginx."nginx.ingress.kubernetes.io/rewrite-target" | string | `"/"` | destination addr for route |
| ingress.annotations.nginx."nginx.ingress.kubernetes.io/ssl-redirect" | string | `"true"` | Redirect http to https  |
| ingress.annotations.tls."kubernetes.io/tls-acme" | string | `"true"` | use acme cert if available |
| ingress.annotations.traefik."traefik.ingress.kubernetes.io/redirect-entry-point" | string | `"https"` | Redirect to https |
| ingress.annotations.traefik."traefik.ingress.kubernetes.io/redirect-permanent" | string | `"true"` | Redirect to https permanently |
| ingress.annotations.traefik."traefik.ingress.kubernetes.io/rule-type" | string | `"PathPrefixStrip"` | rule type |
| ingress.enabled | bool | `false` | attempts to configure ingress if true |
| ingress.hostPrefix.broker | string | `"broker."` | mqtt route subdomain |
| ingress.hostPrefix.rest | string | `"api."` | api (REST) route subdomain |
| ingress.hostPrefix.ui | string | `"dashboard."` | ui route subdomain |
| ingress.tls.enabled | bool | `true` |  |
| ingress.tls.issuerName | string | `"letsencrypt-prod"` |  |
| mq.replicas | int | `2` | how many MQTT replicas to create |
| mq.singlenode | bool | `false` |  |
| mq.storageSize | string | `"128Mi"` |  |
| nameOverride | string | `""` | override the name for netmaker objects  |
| podAnnotations | object | `{}` | pod annotations to add |
| podSecurityContext | object | `{}` | pod security contect to add |
| postgresql-ha.persistence.size | string | `"1Gi"` | size of postgres DB |
| postgresql-ha.postgresql.database | string | `"netmaker"` | postgress db to generate |
| postgresql-ha.postgresql.password | string | `"netmaker"` | postgres pass to generate |
| postgresql-ha.postgresql.replicaCount | int | `2` | postgress number of replicas to deploy |
| postgresql-ha.postgresql.username | string | `"netmaker"` | postgres user to generate |
| replicas | int | `3` | number of netmaker server replicas to create  |
| service.mqPort | int | `31883` | port for MQTT service |
| service.restPort | int | `8081` | port for API service |
| service.type | string | `"ClusterIP"` | type for netmaker server services |
| service.uiPort | int | `80` | port for UI service |
| serviceAccount.annotations | object | `{}` | Annotations to add to the service account |
| serviceAccount.create | bool | `true` | Specifies whether a service account should be created |
| serviceAccount.name | string | `""` | Name of SA to use. If not set and create is true, a name is generated using the fullname template |
| setIpForwarding.enabled | bool | `true` |  |
| ui.replicas | int | `2` | how many UI replicas to create |
| wireguard.enabled | bool | `true` | whether or not to use WireGuard on server |
| wireguard.kernel | bool | `false` | whether or not to use Kernel WG (should be false unless WireGuard is installed on hosts). |
| wireguard.networkLimit | int | `10` | max number of networks that Netmaker will support if running with WireGuard enabled |

## Changelog

### Version 0.2.0

### Older versions

A historical overview of changes can be found on [ArtifactHUB](https://artifacthub.io/packages/helm/k8s-at-home/netmaker?modal=changelog)

## Support

- See the [Docs](https://docs.k8s-at-home.com/our-helm-charts/getting-started/)
- Open an [issue](https://github.com/k8s-at-home/charts/issues/new/choose)
- Ask a [question](https://github.com/k8s-at-home/organization/discussions)
- Join our [Discord](https://discord.gg/sTMX7Vh) community

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v0.1.1](https://github.com/k8s-at-home/helm-docs/releases/v0.1.1)
