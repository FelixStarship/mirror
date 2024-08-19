# 使用 CentOS 最新的基础镜像
FROM centos:latest

# 更新系统并安装 nfs-utils 和 rpcbind
RUN yum update -y && \
    yum install -y nfs-utils rpcbind

# 启动 rpcbind 服务
RUN systemctl enable rpcbind && \
    systemctl start rpcbind

# 启动 NFS 服务
RUN systemctl enable nfs-server && \
    systemctl start nfs-server

# 配置防火墙以允许 NFS 相关的服务
RUN firewall-cmd --permanent --add-service=nfs && \
    firewall-cmd --permanent --add-service=rpc-bind && \
    firewall-cmd --permanent --add-service=mountd && \
    firewall-cmd --reload

# 配置 /etc/exports 文件
COPY ./exports /etc/exports

# 设置正确的文件权限
RUN chmod 644 /etc/exports

# 重启 NFS 服务以应用配置更改
CMD ["systemctl", "restart", "nfs-server"]
