1. Deploy files one be one
```
kubectl apply -f application-config-cm.yaml
kubectl apply -f nginx-html-folder-cm.yaml
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl apply -f ingress.yaml
```

2. Check the value in the Pod, either throug browser `localhost` or check the pod names.

2. Modify value within `application-config-cm.yaml` and reapply
```
kubectl apply -f application-config-cm.yaml
```

2. Compare the results in brower of pods list. Expected - changes in CM are not affecting running Pods.

2. Enforce Pods restart e.g. `kubectl delete pods -l tier=web`

2. Test again. Expected changes are visible in browser as soon as new Pod instance are up and running.

2. Clean up the mess, removing all individual objects
```
kubectl delete -f ingress.yaml
kubectl delete -f service.yaml
kubectl delete -f deployment.yaml
kubectl delete -f application-config-cm.yaml
kubectl delete -f nginx-html-folder-cm.yaml
```