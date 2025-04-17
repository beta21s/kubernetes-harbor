# kubernetes-harbor

### Cài đặt Helm

```
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash
```

### Thêm repo Helm Harbor
```
helm repo add harbor https://helm.goharbor.io
helm repo update
```

### Tạo namespace cho Harbor

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

Kết quả như hình sau
```
root@k8s-master:~# kubectl get svc -n harbor
NAME                TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)             AGE
harbor              NodePort    10.111.0.127     <none>        30003:30002/TCP     4h
harbor-core         ClusterIP   10.105.184.243   <none>        80/TCP              4h
harbor-database     ClusterIP   10.107.61.238    <none>        5432/TCP            4h
harbor-jobservice   ClusterIP   10.98.43.138     <none>        80/TCP              4h
harbor-portal       ClusterIP   10.103.168.97    <none>        80/TCP              4h
harbor-redis        ClusterIP   10.96.39.146     <none>        6379/TCP            4h
harbor-registry     ClusterIP   10.97.118.189    <none>        5000/TCP,8080/TCP   4h
harbor-trivy        ClusterIP   10.109.27.125    <none>        8080/TCP            4h
```

Kết quả sẽ có dịch vụ harbor với NodePort 30003
```
http://<YOUR_LOCAL_IP>:30002
```

Username mặc định: admin
Password: Harbor12345 (hoặc password bạn đặt trong file YAML)

### Login vào Habor private CLI

```
docker login <YOUR_LOCAL_IP>:30002
```




