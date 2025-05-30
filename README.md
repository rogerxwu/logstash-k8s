# logstash-k8s

# Prerequisites
Install rancher

Kubectl CLI isntalled and point to rancher

Helm installed

Config kubectl connect to rancher desktop
```
xianwu@macbookpro .kube % kubectl get nodes
NAME                   STATUS   ROLES                  AGE    VERSION
lima-rancher-desktop   Ready    control-plane,master   4m6s   v1.32.5+k3s1
```

# Deployment
1. Create name space logstash
```
kubectl create namespace logstash
```
2. Add Elastic Helm repo
```
# add elastic repo
xianwu@macbookpro .kube % helm repo add elastic https://helm.elastic.co
"elastic" has been added to your repositories
xianwu@macbookpro .kube % helm repo update
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "elastic" chart repository
Update Complete. ⎈Happy Helming!⎈

# add opensearch repo
xianwu@macbookpro .kube % helm repo add opensearch https://opensearch-project.github.io/helm-charts/
"opensearch" has been added to your repositories
xianwu@macbookpro .kube % helm repo update
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "opensearch" chart repository
...Successfully got an update from the "elastic" chart repository
Update Complete. ⎈Happy Helming!⎈
```

3. Create docker image for logstash
```
docker build
```

4. Create Chart for logstash
```
helm create logstash
cd logstash
```

5. Deploy
```
helm install logstash ./logstash -n logstash

# udpate
helm upgrade logstash ./logstash -n logstash
```

6. Verify

7. Delete
```
helm uninstall logstash -n logstash

```
8. Debug
```
# Enter pod
kubectl exec -it logstash-864d66cb59-7fpsc -n logstash -- bash

kubectl get svc logstash -n logstash
```

