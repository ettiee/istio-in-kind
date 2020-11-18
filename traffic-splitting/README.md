# Splitting traffic to multiple application versions

Deploy v2 of the frontend app which returns a different response to v1:

```
kubectl apply -f frontend-v2.yaml
```

To route traffic between v1 and v2 we will need to update the VirtualService to have 2 routes and a weighting strategy. We will also need to add a DestinationRule:

```
kubectl apply -f traffic-spliting.yaml
```

Now when you send requests you should intermittently see responses from v1/v2 (determined by the weights to each route and LoadBalancer algorithm in the DestinationRule trafficPolicy):

```
➜  ~ curl 127.0.0.1/frontend
"Hi from frontend version 1"
➜  ~ curl 127.0.0.1/frontend
"Hi from frontend version 2"
```
