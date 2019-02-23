# ingress

- apply
```bash
kubectl apply -f https://raw.githubusercontent.com/scylhy/ingress/master/rc.yaml
kubectl apply -f https://raw.githubusercontent.com/scylhy/ingress/master/svc.yaml

kubectl apply -f https://raw.githubusercontent.com/scylhy/ingress/master/backends.yaml
kubectl apply -f https://raw.githubusercontent.com/scylhy/ingress/master/rule.yaml
```
- test
```bash
[root@cce-demo1522483688765-00274 tmp]# kubectl get svc -ningress-nginx
NAME            TYPE       CLUSTER-IP       EXTERNAL-IP   PORT(S)                      AGE
ingress-nginx   NodePort   10.247.160.254   <none>        80:30674/TCP,443:30130/TCP   3h
[root@cce-demo1522483688765-00274 tmp]# curl -H "Host: my.kubernetes.example" 10.247.160.254/webapp1
<h1>This request was processed by host: webapp1-6b8db97858-fsh2h</h1>
[root@cce-demo1522483688765-00274 tmp]# curl -H "Host: my.kubernetes.example" 10.247.160.254/webapp2
<h1>This request was processed by host: webapp2-666dd48bb4-6z44w</h1>
[root@cce-demo1522483688765-00274 tmp]# curl -H "Host: my.kubernetes.example" 10.247.160.254
<h1>This request was processed by host: webapp3-84b7fd69c8-ljgrg</h1>
[root@cce-demo1522483688765-00274 tmp]# curl 10.247.160.254
<html>
<head><title>404 Not Found</title></head>
<body>
<center><h1>404 Not Found</h1></center>
<hr><center>nginx/1.15.6</center>
</body>
</html>
[root@cce-demo1522483688765-00274 tmp]# 
```
