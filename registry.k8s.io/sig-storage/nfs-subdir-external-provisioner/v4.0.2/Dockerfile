FROM centos:7

# 安装软件包和设置SSH服务
RUN yum -y update
RUN yum -y install openssh-server net-tools lsof telnet passwd openssh-clients
RUN echo '123456' | passwd --stdin root
RUN sed -i 's/UsePAM yes/UsePAM no/g' /etc/ssh/sshd_config
RUN sed -ri '/^session\s+required\s+pam_loginuid.so/ s/^/#/' /etc/pam.d/sshd
RUN ssh-keygen -t rsa -A
RUN mkdir -p /root/.ssh && chown root.root /root && chmod 700 /root/.ssh

# 暴露SSH服务端口
EXPOSE 22

# 启动SSH服务
CMD ["/usr/sbin/sshd", "-D"]
