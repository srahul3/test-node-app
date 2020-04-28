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
