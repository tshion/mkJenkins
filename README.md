# mkJenkins
> 個人的なJenkins 環境の開発リポジトリ


## 構築手順
1. `docker network create jenkins`
1. `docker build -t mkjenkins:????.??.?? .`
1.
    ``` shell
    docker run \
        --name jenkins-blueocean \
        --restart=on-failure \
        --detach \
        --network jenkins \
        --env DOCKER_HOST=tcp://docker:2376 \
        --env DOCKER_CERT_PATH=/certs/client \
        --env DOCKER_TLS_VERIFY=1 \
        --publish 8080:8080 \
        --publish 50000:50000 \
        --volume jenkins-data:/var/jenkins_home \
        --volume jenkins-docker-certs:/certs/client:ro \
        mkjenkins:????.??.??
    ```


## 参考文献
* https://www.jenkins.io/doc/book/installing/docker/
