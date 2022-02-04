# tfc-openshift

This is a TF-controller example for OpenShift.

To bootstrap this example, simply copy-n-paste the following snippet
to OpenShift's YAML import and click "Create".

```yaml
---
apiVersion: source.toolkit.fluxcd.io/v1beta1
kind: GitRepository
metadata:
  name: tfc-openshift
  namespace: flux-system
spec:
  interval: 1m0s
  ref:
    branch: main
  url: https://github.com/tf-controller/tfc-openshift.git
---
apiVersion: kustomize.toolkit.fluxcd.io/v1beta2
kind: Kustomization
metadata:
  name: tfc-openshift
  namespace: flux-system
spec:
  interval: 10m0s
  path: ./c00-dev-cluster
  prune: true
  sourceRef:
    kind: GitRepository
    name: tfc-openshift
```
