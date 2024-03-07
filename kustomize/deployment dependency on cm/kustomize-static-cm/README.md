1. Deploy files as group
```
kubectl apply -k .
```

2. Check the value in the Pod, either throug browser `localhost` or check the pod names.

2. Modify value within `application-config-cm.yaml` and reapply all
```
kubectl apply -k .
```

2. Compare the results in brower of pods list. **Changes in CM are not affecting running Pods**.

2. Change the value for `DUMMY` env variable in `deployment.yaml` and reapply all.

2. Test again. Expected changes are visible in browser as soon as new Pod instance are up and running. **Changes in CM requires some form of enforced Pod restart**.

2. Clean up the mess, removing all objects
```
kubectl delete -k .
```

