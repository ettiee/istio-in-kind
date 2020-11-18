# Install istioctl

```
export ISTIO_VERSION=1.7.4
curl -L https://istio.io/downloadIstio | sh -
```

## Install istio to your cluster

Create `istio-system` namespace
```
kubectl apply -f namespace.yaml
```

Deploy istio operator
```
istioctl operator init
```

Install istio to your cluster
```
kubectl apply -f istio-cni.yaml
```

## Verify your istio setup

Verify the health status of the Istio ingress gateway using the endpoint http://localhost:15021/healthz/ready.

```
curl -sI http://localhost:15021/healthz/ready
```
should return

```
HTTP/1.1 200 OK
date: Fri, 17 Jul 2020 19:06:19 GMT
x-envoy-upstream-service-time: 1
server: envoy
transfer-encoding: chunked
```
