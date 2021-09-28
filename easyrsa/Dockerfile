FROM centos:7

RUN yum update -y \
    && yum install -y epel-release \
    && yum install -y easy-rsa \
    && yum clean all

ENV PATH="/usr/share/easy-rsa/3:${PATH}"
ENV EASYRSA_PKI='/usr/local/ca/pki'