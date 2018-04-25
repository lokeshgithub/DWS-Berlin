This is demo for running Spark deep learning pipelines in HDP 3.0 cluster. With Docker enabled YARN cluster, users can run Spark applications with user specified Docker image to customize dependent Python libraries and GPU environment doesn't need to be installed on/pollute the host environment.

## Build Docker image

Build an image from a [Dockerfile](Dockerfile):
```
docker build -t "deep-centos7:1.3.0" .
```
Then tag the image and push it to the registry:
```
docker tag deep-centos7:1.3.0 registry-host/deep-centos7:1.3.0
docker push registry-host/deep-centos7:1.3.0
```

## Update Spark job configuration

```
spark.yarn.appMasterEnv.YARN_CONTAINER_RUNTIME_DOCKER_CONTAINER_NETWORK=host
spark.yarn.appMasterEnv.YARN_CONTAINER_RUNTIME_DOCKER_IMAGE=registry-host/deep-centos7:1.3.0
spark.yarn.appMasterEnv.YARN_CONTAINER_RUNTIME_DOCKER_MOUNTS=/etc/passwd:/etc/passwd:ro,/etc/krb5.conf:/etc/krb5.conf:ro
spark.yarn.appMasterEnv.YARN_CONTAINER_RUNTIME_TYPE=docker
spark.executorEnv.YARN_CONTAINER_RUNTIME_DOCKER_CONTAINER_NETWORK=host
spark.executorEnv.YARN_CONTAINER_RUNTIME_DOCKER_IMAGE=registry-host/deep-centos7:1.3.0
spark.executorEnv.YARN_CONTAINER_RUNTIME_DOCKER_MOUNTS=/etc/passwd:/etc/passwd:ro,/etc/krb5.conf:/etc/krb5.conf:ro
spark.executorEnv.YARN_CONTAINER_RUNTIME_TYPE=docker
```

## Run demo

We have two demos:
* [Feature transformer](https://drive.google.com/open?id=1B-0aUPrpb-vd4ssFdBVXwxP65dzZI9yE)
* [Transfer learning](https://drive.google.com/open?id=1LlKmnxblkYk8je-KUjOkVDBhYSuCn1a3)
