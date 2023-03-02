FROM openjdk:11

RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install \
        maven \
        openssh-client \
        docker.io -y

RUN apt-get clean

RUN groupadd --gid 116 jenkins && \
    useradd --uid 110 --gid jenkins --shell /bin/bash --create-home jenkins

ADD id_rsa /home/jenkins/.ssh/id_rsa
#ADD id_rsa /root/.ssh/ 
RUN chmod 777 /home/jenkins/.ssh
#RUN chmod 600 /root/.ssh/