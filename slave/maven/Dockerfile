FROM centos:8

RUN cd /etc/yum.repos.d/
RUN sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
RUN sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*

RUN yum install openssh-server -y

RUN adduser jenkins && \
    echo "jenkins:jenkins" | chpasswd

RUN mkdir /home/jenkins/.ssh
RUN mkdir /home/jenkins/.m2
RUN chmod 700 /home/jenkins/.ssh

COPY slave.pub /home/jenkins/.ssh/authorized_keys

RUN chown jenkins:jenkins -R /home/jenkins/.m2
RUN chown jenkins:jenkins -R /home/jenkins/.ssh/
RUN chmod 600 /home/jenkins/.ssh/authorized_keys

RUN rm -f /run/nologin

RUN yum update -y && \
    yum install -y git && \
    yum install -y net-tools && \
    yum install -y java-11-openjdk-devel && \
    yum install -y maven

RUN ssh-keygen -A

CMD /usr/sbin/sshd -D
