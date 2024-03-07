1. Check content of `kustomization.yaml` and make sure that name suffix hash is disabled. Following lines should be available and uncommented.
```
generatorOptions:
  disableNameSuffixHash: true
```

2. Deploy files as group
```
kubectl apply -k .
```

3. Check the value in the Pod, either throug browser `localhost` or check the Pods names.

3. Modify value within `application-config.properties` and reapply all
```
kubectl apply -k .
```

4. Compare the results in brower of pods list. **Changes in CM are not affecting running Pods.**

4. Enable the name suffic hashing, either removing or commenting out the below section in `kustomization.yaml`
```
#generatorOptions:
#  disableNameSuffixHash: true
```

6. Apply changes. Than go back to experiments with the propeties in `application-config.properties`. **Changes in CM that are accompanied by change of CM object reference (dynamic CM name) are enforcing Pod restart.**

7. Clean up the mess, removing all objects
```
kubectl delete -k .
```