# helm-demodude repo

Thanks for checking out my helm chart! This is a way to serve my app demodude, found [here](https://github.com/zipforth/demodude)

## To pull the chart:
- `helm repo add zipforth-repo https://zipforth.github.io/helm-demodude/`
- `helm repo update zipforth-repo`
## Installing the chart
- The default behavior is setting up a clusterIP service, which serves a 1 replica deployment. install with `helm install demodude zipforth-repo/helm-demodude`
- For adjusting the default values, see the below table:

| Name                     | Description                                                | Default Value                       | Required? |
|--------------------------|------------------------------------------------------------|-------------------------------------|-----------|
| images.demodude          | The image of the demodude app                              | ghcr.io/zipforth/demodude:\<release\> | Y         |
| svc.type                 | The type of service used: choose ClusterIP or NodePort     | ClusterIP                           | Y         |
| svc.port                 | The port the service should use                            | 80                                  | Y         |
| svc.targetPort           | The target port the service points to, required to be 9999 | 9999                                | Y         |
| svc.nodeport             | Not currently used                                         | ""                                  | N         |
| svc.name                 | The name of the nodeport                                   | demodude-svc                        | Y         |
| ingress.add_ingress      | If using an ingress to serve the app externally            | false                               | Y         |
| ingress.host             | the host for the ingress to direct                         | ""                                  | N         |
| ingress.ingressClassName | the ingress class to use for the ingress                   | ""                                  | N         |