FROM debian:stable-slim

RUN mkdir -p /usr/share/man/man1 /usr/share/man/man2

RUN apt-get update && \
apt-get install -y --no-install-recommends curl git python3 python3-pip openjdk-11-jre bzip2 build-essential vim emac\    && apt-get clean

RUN apt-get install -y --no-install-recommends \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

RUN apt-get update	

RUN pip3 install --upgrade pip
RUN pip3 install miniwdl
RUN pip3 install setuptools
RUN pip3 install croo --upgrade

COPY caper caper
ENV PATH="${PATH}:${PWD}/caper/bin"


COPY juicer juicer
RUN cp -r juicer/CPU/common /usr/local/bin
ENV PATH="${PATH}:${PWD}/juicer/CPU/common"


COPY pairix pairix
ENV PATH="${PATH}:${PWD}/pairix/bin"
RUN cp pairix/bin/pairix pairix/bin/bgzip /usr/local/bin && cp /pairix/util/bam2pairs/bam2pairs /usr/local/bin

COPY encodedcc_hic/hic_pipeline hic_pipeline
ENV PATH="${PATH}:${PWD}/hic_pipeline"

# For sorting, LC_ALL is C
ENV LC_ALL C

