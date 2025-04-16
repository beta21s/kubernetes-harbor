# kubernetes-harbor

### Helm

```
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash
```

### repo Helm Harbor
```
helm repo add harbor https://helm.goharbor.io
helm repo update
```

### namespace cho Harbor

```
kubectl create namespace harbor
```

### Cài đặt

```
helm install harbor harbor/harbor -f harbor-values.yaml --namespace harbor
helm install harbor harbor/harbor -f harbor-values-harbor.yaml --namespace harbor
```

### Kiểm tra

```
kubectl get svc -n harbor
```

Kết quả sẽ có dịch vụ harbor với NodePort 30003
```
http://<YOUR_LOCAL_IP>:30002
```


Username mặc định: admin
Password: Harbor12345 (hoặc password bạn đặt trong file YAML)

