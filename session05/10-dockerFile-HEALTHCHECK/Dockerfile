FROM centos:7
RUN yum install -y httpd curl
HEALTHCHECK --interval=2m --timeout=3s CMD curl 127.0.0.1 || exit 1
ENTRYPOINT /usr/sbin/httpd && /bin/bash
