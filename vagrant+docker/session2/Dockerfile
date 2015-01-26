FROM ubuntu:14.04
MAINTAINER Daisuke Ikeda <dai.ikd123@gmail.com>

## Install packages ##
RUN apt-get update
RUN apt-get install -y openssh-server
RUN mkdir /var/run/sshd

## Setup login user ##
RUN useradd docker
RUN echo "docker:password" | chpasswd
RUN echo "docker ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers.d/docker

## Setup sshd config ##
RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config
RUN sed -ri 's/#UsePAM no/UsePAM no/g' /etc/ssh/sshd_config

## Start sshd ##
RUN service ssh start

## Open Port ##
EXPOSE 22

## Set entrypoint ##
CMD [ "/usr/sbin/sshd", "-D" ]
