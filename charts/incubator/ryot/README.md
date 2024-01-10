# ryot

![Version: 0.0.1](https://img.shields.io/badge/Version-9.1.3-informational?style=flat-square) ![AppVersion: 4.0.0](https://img.shields.io/badge/AppVersion-1.8.0-informational?style=flat-square)

Ryot - Roll your own tracker

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/homelab-ci/charts/issues/new/choose)**

## Source Code

* <https://github.com/IgnisDa/ryot>

## Requirements

Kubernetes: `>=1.16.0-0`

## Dependencies

| Repository                            | Name | Version |
|---------------------------------------|------|---------|
| https://charts.bitnami.com/bitnami    | postgresql | 11.6.12 |
| https://homelab-ci.github.io/library-ezUxewsl | common | 4.5.2 |

## TL;DR

```console
helm repo add homelab-ci https://homelab-ci.com/charts/
helm repo update
helm install ryot homelab-ci/ryot
```

## Installing the Chart

To install the chart with the release name `ryot`

```console
helm install ryot homelab-ci/ryot
```

## Uninstalling the Chart

To uninstall the `ryot` deployment

```console
helm uninstall ryot
```

The command removes all the Kubernetes components associated with the chart **including persistent volumes** and deletes the release.

## Configuration

Read through the [values.yaml](./values.yaml) file. It has several commented out suggested values.
Other values may be used from the [values.yaml](https://github.com/homelab-ci/library-charts/tree/main/charts/stable/common/values.yaml) from the [common library](https://github.com/homelab-ci/library-charts/tree/main/charts/stable/common).

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

```console
helm install ryot \
  --set env.TZ="America/New York" \
    homelab-ci/ryot
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart.

```console
helm install ryot homelab-ci/ryot -f values.yaml
```

## Custom configuration
N/A

## Values

**Important**: When deploying an application Helm chart you can add more values from our common library chart [here](https://github.com/homelab-ci/library-charts/tree/main/charts/stable/common)

| Key                    | Type | Default                                                                                                                                                                                                 | Description |
|------------------------|------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| env                    | object | See below                                                                                                                                                                                               | See the following files for additional environment variables: https://ignisda.github.io/ryot/configuration.html |
| env.DATABASE_URL       | string | `"postgres://{{ .Values.postgresql.auth.username }}:{{ .Values.postgresql.auth.password }}@{{ include \"common.names.fullname\" .}}-postgresql/{{ .Values.postgresql.auth.database }}?sslmode=disable"` | Postgresql connection parameters. See [lib/pq](https://pkg.go.dev/github.com/lib/pq#hdr-Connection_String_Parameters) for more details. |
| image.pullPolicy       | string | `"IfNotPresent"`                                                                                                                                                                                        | image pull policy |
| image.repository       | string | `"ghcr.io/ignisda/ryot"`                                                                                                                                                                                | image repository |
| image.tag              | string | `latest`                                                                                                                                                                                                | image tag |
| ingress.main           | object | See values.yaml                                                                                                                                                                                         | Enable and configure ingress settings for the chart under this key. |
| postgresql             | object | See values.yaml                                                                                                                                                                                         | Enable and configure postgresql database subchart under this key.    For more options see [postgresql chart documentation](https://github.com/bitnami/charts/tree/master/bitnami/postgresql) |
| postgresql.persistence | object | See values.yaml                                                                                                                                                                                         | Enable and configure postgresql database subchart under this key.    For more options see [postgresql chart documentation](https://github.com/bitnami/charts/tree/master/bitnami/postgresql) |
| service                | object | See values.yaml                                                                                                                                                                                         | Configures service settings for the chart. |

## Changelog

### Version 0.0.1

#### Added

N/A

#### Changed

N/A

#### Fixed

N/A

### Older versions

A historical overview of changes can be found on [ArtifactHUB](https://artifacthub.io/packages/helm/homelab-ci/ryot?modal=changelog)

## Support

- See the [Docs](https://docs.homelab-ci.com/our-helm-charts/getting-started/)
- Open an [issue](https://github.com/homelab-ci/charts/issues/new/choose)
- Ask a [question](https://github.com/homelab-ci/organization/discussions)
- Join our [Discord](https://discord.gg/sTMX7Vh) community

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v0.1.1](https://github.com/homelab-ci/helm-docs/releases/v0.1.1)