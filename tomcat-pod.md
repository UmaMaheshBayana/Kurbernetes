1) Create tomcat-pod.yml file the Kops machine.

```
sudo vi tomcat-pod.yml
````
2) Past the below lines in the file and save the file
```
---
apiVersion: v1
kind: Pod
metadata:
  name: tomcat
  labels:
    app: tomcat
spec:
    containers:
       - name: tomcat
         image: tomcat:8.0
         ports:
           - containerPort: 8080
````

3) create the pod using cmd
```
kubectl create -f tomcat-pod.yml
````
4) Check running pods
```
kubectl get pods
````
5) Check the pod details
```
kubectl describe $PODNAME
````
