FROM quay.io/mhildenb/container-workshop-base:latest as podmandevcontainer

USER root

RUN pip3 install --upgrade boto3 boto kubernetes openshift

# make python 3 the default python (that ansible uses)
RUN ln -s /usr/bin/python3 /usr/bin/python

# for htpasswd utility
RUN yum -y install httpd-tools && yum clean all

RUN curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.rpm.sh | bash \
    && yum -y install git-lfs

COPY cdk-requirements.txt /tmp
RUN npm install -g aws-cdk && pip3 install -r /tmp/cdk-requirements.txt

from podmandevcontainer as devcontainer

USER default
