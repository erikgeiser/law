FROM centos:centos7

# environment variables
ENV WORKDIR /root/law

# copy files
COPY entrypoint.sh /root/entrypoint.sh

# install software
RUN yum -y update; yum clean all
RUN yum -y install epel-release; yum clean all
RUN yum -y install which nano screen wget git; yum clean all
RUN yum -y install install python-setuptools; yum clean all
RUN easy_install pip
RUN yum -y install gfal2-all gfal2-python; yum clean all

# install python packages
RUN pip install luigi six

# load the law code
RUN git clone https://github.com/riga/law $WORKDIR

# the workdir
WORKDIR /root/law

# expose ports
EXPOSE 8082

# entry point
ENTRYPOINT ["bash", "/root/entrypoint.sh"]