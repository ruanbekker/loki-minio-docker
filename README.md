# loki-minio-docker
Basic example of Loki, Minio and BoltDB on Docker

## Usage

Boot:

```
$ docker-compose up --remove-orphans -d
```

Grafana is available at http://localhost:3000 and Minio at http://localhost:9000


Minio Credentials:

```
access key: 697d0993dd097f38d5b8
secret key: 9f88738761b57c63f6a81bdfd471
```

App Endpoints:

```
$ curl http://localhost:8080/
$ curl http://localhost:8080/ping
```

Screenshot of Loki:

![image](https://user-images.githubusercontent.com/567298/95169279-eacfeb80-07b2-11eb-89df-68f6d2195c3d.png)

Screenshot of Minio:

![image](https://user-images.githubusercontent.com/567298/95172885-3c2ea980-07b8-11eb-90eb-a9f5b32c6412.png)
