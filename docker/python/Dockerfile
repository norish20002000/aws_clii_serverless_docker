FROM python:3.7
# USER root

ARG AWS_ACCESS_KEY_ID
ARG AWS_SECRET_ACCESS_KEY

RUN apt-get update -y && apt-get upgrade -y \
  && apt-get install -y \
  zlib1g-dev \
  build-essential \
  vim \
  less \ 
  git \
  zip \
  unzip \
  jq \
  locales && \
  localedef -f UTF-8 -i ja_JP ja_JP.UTF-8
ENV LANG ja_JP.UTF-8
ENV LANGUAGE ja_JP:ja
ENV LC_ALL ja_JP.UTF-8
ENV TZ JST-9
ENV TERM xterm

# Install Nodejs 8
RUN curl -sL https://deb.nodesource.com/setup_14.x | bash -
# RUN apt-get install -y nodejs npm
RUN apt-get install -y nodejs && \
  npm install -g npm@latest

# エイリアス
RUN echo 'alias ll="ls -l"' >> ~/.bashrc

RUN pip install --upgrade pip
RUN pip install --upgrade setuptools

# install aws-cli
RUN pip install awscli
# install boto3
RUN pip install boto3
# install serverless framework
RUN npm install -g serverless
# set aws key 
RUN sls config credentials --provider aws --key $AWS_ACCESS_KEY_ID --secret $AWS_SECRET_ACCESS_KEY
# default region
RUN aws configure set region ap-northeast-1
