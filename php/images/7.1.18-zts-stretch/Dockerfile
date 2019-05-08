FROM circleci/php:7.1.18-zts-stretch-node

USER root

RUN apt-get update \
    && apt-get install python3-pip python3-dev python3-venv build-essential ruby apt-transport-https \
    && npm install -g grunt grunt-contrib-sass sass \
    && pip3 install awscli awsebcli boto3

RUN ( curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add - ) \
    && ( echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | tee -a /etc/apt/sources.list.d/kubernetes.list ) \
    && apt-get update && apt-get install -y kubectl gettext libmcrypt-dev \
    && sudo pecl channel-update pecl.php.net \
    && yes | sudo pecl install mcrypt-1.0.0 \
    && docker-php-ext-enable mcrypt \
    && curl -s -o /usr/local/bin/aws-iam-authenticator https://amazon-eks.s3-us-west-2.amazonaws.com/1.11.5/2018-12-06/bin/linux/amd64/aws-iam-authenticator \
    && chmod +x /usr/local/bin/aws-iam-authenticator

USER circleci