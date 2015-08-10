FROM ubuntu:14.04
MAINTAINER Derek Bourgeois <derek@ibourgeois.com>

RUN sed -i 's/# \(.*multiverse$\)/\1/g' /etc/apt/sources.list

RUN apt-get update
RUN apt-get -y upgrade

RUN apt-get install -y build-essential
RUN apt-get install -y software-properties-common
RUN apt-get install -y curl
RUN apt-get install -y git
RUN apt-get install -y unzip
RUN apt-get install -y nano
RUN apt-get install -y wget

RUN rm -rf /var/lib/apt/lists/*

ADD config/.bashrc /root/.bashrc

ENV HOME /root

WORKDIR /root

CMD ["bash"]
