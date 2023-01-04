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
6) Create tomcatservice-pod.yml on the kops machine
```
sudo vim tomcatservice-pod.yml
````
7) Paste below line in the file and save
```
---
apiVersion: v1
kind: Service
metadata:
   name: tomcat
spec:
   ports:
   - port: 8090
     nodePort: 30001
     targetPort: 8080
     protocol: TCP
   selector:
       app: tomcat
   type: NodePort
````
8) Run the service yml file
```
kubectl create -f tomcatservice-pod.yml 
````
9) cmd to check the services running and stoped
```
kubectl get svc
````
10)  CMD to know more details of the running service
```
kubectl describe svc $SERVICE_NAME
````
11) CMD to check the running pod IP address, and tally the IP in services with Pod IP
```
kubectl describe pob | grep IP
````
12) Now change the EC2 node machine security groups as the Nodeport mentioned and open the tomcat with machie IP address with port.
