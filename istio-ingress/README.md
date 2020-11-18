# Ingress example

This example shows you how to run a simple application and provide an ingress from your local machine to your application in kind through the istio mesh.


Create namespace for your shiny new application
```
kubectl apply -f namespace.yaml
```

Create deployment/service for your new application
```
kubectl apply -f frontend.yaml
```

NB: if you watch the pod come up for your deployment you should see 2 containers in that pod - one is your application container, and the other is the envoy proxy for the istio mesh. Istio sidecar is configured by a webhook when you create the deployment because we have set the label `istio-injection: enabled` on the apps namespace.

To route traffic to the frontend application we need to create a Gateway and a VirtualService. Run

```
kubectl apply -f ingress.yaml
```

Now you should be able to reach your service:
```
curl 127.0.0.1/frontend
"Hi from frontend version 1"
```
