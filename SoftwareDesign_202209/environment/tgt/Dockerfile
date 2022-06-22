FROM quay.io/centos/centos:stream8
RUN dnf install -y openssh-server hostname
RUN systemctl enable sshd
RUN echo password | passwd --stdin root
CMD ["/sbin/init"]