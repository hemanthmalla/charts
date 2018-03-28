# Diffy

Find potential bugs in your services without writing tests.

* https://github.com/twitter/diffy

## Chart Details

This chart will deploy:

* 2 copies of your last known stable codebase (primary and secondary)
* Candidate, whose changes need to be tested
* Diffy proxy and dashboard services

## Installing the Chart

To install the chart with the release name `my-service`:

```bash
$ kubectl create namespace diffy
$ helm install --name my-service incubator/diffy --namespace=diffy
```

## Configuration

The following tables lists the configurable parameters of the Diffy chart and their default values.

| Parameter                         | Description                          | Default                                                                      |
| --------------------------------- | ------------------------------------ | ---------------------------------------------------------------------------- |
| `stable.image.repository`         | Image used for Primary and Secondary | `diffy/example-service`                                                      |
| `stable.image.tag`                | Image tag for Primary and Secondary  | `production`                                                                 |
| `stable.containerPort`            | TCP port on which the stable service listens on  | `9000`                                                           |
| `stable.service.type`             | Kubernetes service type              | `ClusterIP`                                                                  |
| `candidate.image.repository`      | Image used for Candidate             | `diffy/example-service`                                                      |
| `candidate.image.tag`             | Image tag for Candidate              | `production`                                                                 |
| `candidate.containerPort`         | TCP port on which the candidate service listens on  | `9000`                                                        |
| `candidate.service.type`          | Kubernetes service type              | `ClusterIP`                                                                  |
| `diffy.image.repository`          | Image used for Diffy service         | `diffy/diffy`                                                                |
| `diffy.image.tag`                 | Image tag for Diffy service          | `latest`                                                                     |
| `diffy.service.type`              | Kubernetes service type              | `ClusterIP`                                                                  |


Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```bash
$ helm install --name my-service -f values.yaml incubator/diffy
```

Diffy installation can be delete with : 

```bash
$ helm del --purge my-service
```