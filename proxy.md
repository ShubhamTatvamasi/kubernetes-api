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
  namespace: default
spec:
  containers:
  - image: nginx:alpine
    name: nginx
EOF
```

Deploy pod using API:
```bash
HOST=http://127.0.0.1:8001

curl ${HOST}/api/v1/namespaces/project1/pods \
  -H "Content-Type: application/yaml" \
  --data-binary @pod.yaml
```
