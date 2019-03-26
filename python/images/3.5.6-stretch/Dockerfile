FROM circleci/python:3.5.6-stretch

# BEGIN IMAGE CUSTOMIZATIONS

# Install pipenv
USER root

RUN apt-get update \
    && apt-get install apt-transport-https \
    && pip3 install awscli awsebcli boto3 pipenv

RUN ( curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add - ) \
    && ( echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | tee -a /etc/apt/sources.list.d/kubernetes.list ) \
    && apt-get update && apt-get install -y kubectl gettext \
    && curl -s -o /usr/local/bin/aws-iam-authenticator https://amazon-eks.s3-us-west-2.amazonaws.com/1.11.5/2018-12-06/bin/linux/amd64/aws-iam-authenticator \
    && chmod +x /usr/local/bin/aws-iam-authenticator

# END IMAGE CUSTOMIZATIONS

USER circleci

CMD ["/bin/sh"]
