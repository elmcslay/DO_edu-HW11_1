FROM openjdk:11

RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install \
        maven \
        openssh-client \
        docker.io -y

RUN apt-get clean

ARG UID=110
ARG GID=116
ENV UID=${UID}
ENV GID=${GID}
RUN usermod -u $UID jenkins && \
    groupmod -g $GID jenkins

ADD id_rsa /home/jenkins/.ssh/id_rsa
RUN chmod 600 /home/jenkins/.ssh/id_rsa