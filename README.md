# test-node-app
A first test node application as docker image

docker build -t srahul3/node-web-app .
docker images

REPOSITORY                                      TAG                 IMAGE ID            CREATED             SIZE
srahul3/node-web-app                            latest              a8e1e569c1ce        19 hours ago        915MB

docker login docker.io
docker push srahul3/node-web-app:latest

docker run -p 49160:8090 -d srahul3/node-web-app
e720aeda22edf03a16c3abcb452af83927b816a07f5efeb314f7401aace03dd9

docker ps
CONTAINER ID        IMAGE                                                     COMMAND                  CREATED             STATUS              PORTS                     NAMES
e720aeda22ed        srahul3/node-web-app                                      "docker-entrypoint.s…"   21 seconds ago      Up 13 seconds       0.0.0.0:49160->8090/tcp   boring_aryabhata

curl -i localhost:49160
HTTP/1.1 200 OK
X-Powered-By: Express
Content-Type: text/html; charset=utf-8
Content-Length: 11
ETag: W/"b-Ck1VqNd45QIvq3AZd8XYQLvEhtA"
Date: Tue, 28 Apr 2020 12:26:02 GMT
Connection: keep-alive

Hello World

---------------------Kubernetes deployment------------------------------

PS D:\rahul\sde\git-repository\test-node-app> kubectl apply -f k8s.yml
deployment.apps/hello-world created
service/hello-world created

PS D:\rahul\sde\git-repository\test-node-app> kubectl get all
NAME                               READY   STATUS    RESTARTS   AGE
pod/hello-world-7c99fd8d68-8g5m9   1/1     Running   0          10m
pod/hello-world-7c99fd8d68-jpthm   1/1     Running   0          14m

NAME                  TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)    AGE
service/hello-world   ClusterIP   10.132.178.55   <none>        8090/TCP   14m

NAME                          READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/hello-world   2/2     2            2           14m

NAME                                     DESIRED   CURRENT   READY   AGE
replicaset.apps/hello-world-7c99fd8d68   2         2         2       14m

On Okteto:
Deployment
hello-world
Running
Overview
Logs
CPU
1.0
 / 
2.0
Memory
2GB
 / 
4GB
Disk
0Bytes
 / 
10GB
Type:
Deployment
Endpoints:
https://hello-world-srahul3.cloud.okteto.net
Replicas:
2
Created:
16 mins ago
Last updated:
12 mins ago
