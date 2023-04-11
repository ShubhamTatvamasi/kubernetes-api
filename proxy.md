# proxy

Start the kube proxy service:
```bash
kubectl proxy
```

Create a pod file:
```bash
cat > pod.yaml << EOF
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - image: nginx:alpine
    name: nginx
EOF
```

Deploy pod using API:
```bash
HOST=http://127.0.0.1:8001

curl ${HOST}/api/v1/namespaces/default/pods \
  -H "Content-Type: application/yaml" \
  --data-binary @pod.yaml
```
> Note: that the `-X POST` flag can be omitted because the `--data-binary` flag is being used.
