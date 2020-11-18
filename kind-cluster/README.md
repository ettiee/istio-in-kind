# Set up kind cluster


```
chmod +x single-node.sh
./single-node.sh
```

Check that your cluster came up:

```
kubectl config use-context kind-kind
kubectl get all
```

☝️ make sure you can see some k8s resources.
