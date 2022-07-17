# nginx-ansible-operator

Initalize the operator:
```bash
operator-sdk init \
  --domain shubhamtatvamasi.com \
  --plugins ansible
```

Create an API:
```bash
operator-sdk create api \
  --group demo \
  --version v1alpha1 \
  --kind Nginx \
  --generate-role \
  --generate-playbook
```

Set the operator image name:
```bash
export IMG=shubhamtatvamasi/nginx-ansible-operator:0.0.2
```

Build and push operator docker image:
```bash
make docker-build docker-push IMG=${IMG}
```

Install Custom Resource Definition:
```bash
make install
```

Deploy operator:
```bash
make deploy IMG=${IMG}
```

Install Custom Resource:
```bash
kubectl apply -f config/samples/demo_v1alpha1_nginx.yaml
```

### Uninstall

Delete Custom Resource:
```bash
kubectl delete -f config/samples/demo_v1alpha1_nginx.yaml
```

Delete operator:
```bash
make undeploy
```