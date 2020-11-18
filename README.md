# Istio in kind

Simple example running istio in kind.

## Prerequisites

- Install [kind](https://github.com/kubernetes-sigs/kind) (tested with kind version 0.9.0)
- Install [istioctl](https://istio.io/latest/docs/setup/getting-started/#download) (tested with 1.7.4)
- Install [helm 3](https://helm.sh/)

## Running instructions

Run in the following order.

NB: these must be run sequentially, there are resources shared across steps creating dependencies.

1 - [kind-cluster](./kind-cluster)
2 - [istio-install](./instio-install)
3 - [istio-ingress](./istio-ingress)
4 - [traffic-splitting](./traffic-splitting)
