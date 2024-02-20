# DKP Custom Catalog Application: Big Bang

1. Set the K8s context to the DKP management cluster.
2. Set the WORKSPACE_NAME to the relevant namespace as an environmental variable:

```bash
export WORKSPACE_NAME=[your_namespace]
````

Copy and past the following into the terminal to deploy to the DKP catalog:

```bash
kubectl apply -f - <<EOF
apiVersion: source.toolkit.fluxcd.io/v1
kind: GitRepository
metadata:
  name: bigbang 
  namespace: ${WORKSPACE_NAME}
  labels:
    kommander.d2iq.io/gitapps-gitrepository-type: catalog
    kommander.d2iq.io/gitrepository-type: catalog
spec:
  interval: 1m0s
  ref:
    branch: main
  timeout: 20s
  url: https://github.com/bovan01/dkp-bigbang
EOF
```
