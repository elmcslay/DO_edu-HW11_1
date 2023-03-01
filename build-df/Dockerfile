FROM openjdk:11

RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install \
        maven \
        openssh-client \
        docker.io -y

RUN apt-get clean

ADD id_rsa /root/.ssh/id_rsa
RUN chmod 600 /root/.ssh/id_rsa