# docker-zeppelin
Zeppelin v0.9.0-SNAPSHOT


### Launching Zeppelin with Docker in 1 minute

As of 0.7.2, Zeppelin community integrated building docker image into the release process.  
Thus, every release will include its own docker image.

Here is few links might be helpful.

- [Dockerhub: apache/zeppelin](https://hub.docker.com/r/apache/zeppelin/)
- [Dockerfile for Zeppelin (master)](https://github.com/apache/zeppelin/blob/master/scripts/docker/zeppelin/bin/Dockerfile)
- [Documentation (master)](https://github.com/apache/zeppelin/blob/master/docs/install/docker.md)
- [JIRA tickets regarding official docker images](https://issues.apache.org/jira/browse/ZEPPELIN-2667)

#### 1. Requirement

Make sure that docker is installed in the machine where Zeppelin will run on.

- [Installing Docker Community Edition](https://www.docker.com/community-edition/)

#### 2. Getting Started

You can start dockerized Zeppelin with this simple command.

docker run -p 8080:8080 --rm --name zeppelin apache/zeppelin:0.7.2

After executing, try to access 

localhost:8080 in the browser. (Google Chrome is recommended)  
If you are having trouble with accessing the main page, Please clear browser cache.

- [SO: clearing browser cache for a page in chrome develop tool](https://stackoverflow.com/questions/5690269/disabling-chrome-cache-for-website-development)

By default, docker container doesn’t persist any file. As a result you will lose all the notebook that you were working on.  
To persist notes and logs, we can set [docker volumn option](https://docs.docker.com/engine/tutorials/dockervolumes/#mount-a-host-directory-as-a-data-volume)

Here is an example command for that.

docker run -p 8080:8080 --rm -v $PWD/logs:/logs -v $PWD/notebook:/notebook -e ZEPPELIN_LOG_DIR='/logs' -e ZEPPELIN_NOTEBOOK_DIR='/notebook' --name zeppelin apache/zeppelin:0.7.2
