FROM ubuntu:16.04

LABEL maintainer="amir.mohtasebi@gmail.com"

RUN apt-get update

RUN apt-get -y install curl \
    && apt-get -y install unzip \
    && apt-get -y install wget \
    && mkdir /usr/local/terraform \
    && chown -R $(whoami): /usr/local/terraform/ \
    && cd /usr/local/terraform/ \
    && wget -O terraform.zip https://releases.hashicorp.com/terraform/0.11.5/terraform_0.11.5_linux_amd64.zip \
    && unzip terraform.zip \
    && rm terraform.zip \
    && echo export PATH=\$PATH:$(pwd) >> ~/.bashrc \
    && apt-get -y install git-core

RUN apt-get -y install python3 \
    && curl -O https://bootstrap.pypa.io/get-pip.py \
    && python3 get-pip.py --user \
    && echo export PATH=~/.local/bin:$PATH >> ~/.bashrc

RUN ~/.local/bin/pip install awscli --upgrade --user

CMD ["bash"]
