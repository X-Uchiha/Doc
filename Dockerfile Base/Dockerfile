FROM ubuntu:latest

WORKDIR /usr/src/app
SHELL ["/bin/bash", "-c"]
RUN chmod 777 /usr/src/app

RUN apt-get -y update && DEBIAN_FRONTEND="noninteractive" \
    apt-get install -y python3 python3-pip p7zip-full \
    p7zip-rar ffmpeg aria2 locales curl wget git unzip libmagic-dev libcrypto++-dev libssl-dev \ 
    libc-ares-dev libcurl4-openssl-dev libsqlite3-dev libsodium-dev libfreeimage-dev libpq-dev libffi-dev  \
    && locale-gen en_US.UTF-8 && \ 
    curl https://rclone.org/install.sh | bash 

# Installing Mirror-Bot Requirements
COPY requirements.txt .
RUN pip3 install --no-cache-dir -r requirements.txt

RUN apt-get -y update && apt-get -y upgrade && apt-get -y autoremove && apt-get -y autoclean

WORKDIR /usr/src/app
RUN chmod 777 /usr/src/app

RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8
