## Problem statement

We needed to change some configuration pieces that are usually delivered to Pods through envs variables, and are managed externally to the Deployment object.

What is the optimal way to enforce Pods restart on change.

## Analyzis

Kubernetess cluster does not automatically restart Pods that are dependent on explicit ConfigMap resource, after changes to the CM are delivered to cluster.

Operator needs to either enforce Pod restart either by Pod deletion (see ./without-kustomize) or irrelevant changes within Deployment manifest (see ./kustomize-static-cm).

Kustomize with its `configMapGenerator` could be considered a solution, as long as we rely on name-suffix-hashes. A change in source of values within CM yields in new CM name/id which leads to a change in deployment manifest as well.