FROM centos:7

LABEL maintainer="My first test"

RUN yum -y update && yum clean all

RUN yum -y install httpd 

COPY index.html /var/www/html/

EXPOSE 80

ENTRYPOINT [ "/usr/sbin/httpd" ]

CMD [ "-D", "FOREGROUND" ] 