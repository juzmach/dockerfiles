FROM ubuntu:14.04
MAINTAINER Juuso Strömberg <juzmach@gmail.com>
RUN apt-get update
RUN apt-get install -y openssh-server screen irssi mosh oidentd
RUN mkdir /var/run/sshd
ADD .userfile /
RUN newusers .userfile
RUN sed -i 's/PermitRootLogin without-password/PermitRootLogin no/' /etc/ssh/sshd_config
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd
RUN locale-gen en_US
RUN locale-gen en_US.UTF-8
RUN echo "export LANG=en_US.UTF-8" >> /etc/profile
RUN echo "LANGUAGE=en_US.UTF-8" >> /etc/profile
ENV echo "LC_ALL=en_US.UTF-8" >> /etc/profile
EXPOSE 22
EXPOSE 6000/udp
CMD ["/usr/sbin/sshd", "-D"]

