FROM ubuntu:latest

MAINTAINER Eugene de Beste

RUN apt-get update -y && \
    apt-get install --no-install-recommends r-base-core -y && \
    apt-get install -y  \
        build-essential \
        wget \
        zlib1g-dev \
        libblas-dev \
        liblapack-dev \
        gfortran \
        libssl-dev

RUN printf "source('https://bioconductor.org/biocLite.R')\nbiocLite('crlmm')" > script.R
RUN Rscript script.R
RUN rm script.R
