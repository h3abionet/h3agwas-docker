FROM quay.io/cybozu/ubuntu:20.04

ENV PYTHONNOUSERSITE 1

MAINTAINER JTB 

RUN apt-get update -qq
# install two helper packages we need
RUN apt install -y dirmngr apt-transport-https ca-certificates software-properties-common gnupg2  
RUN apt-get update && apt-get install -y apt-transport-https ca-certificates python3-pip python3-dev wget

ENV  R_VERSION 4.0.5
RUN curl -O https://cran.rstudio.com/src/base/R-4/R-${R_VERSION}.tar.gz && tar -xzvf R-${R_VERSION}.tar.gz 

RUN apt-get install -y libx11-dev xserver-xorg-dev libxt-dev
RUN apt-get install build-essential fort77 xorg-dev liblzma-dev libblas-dev gfortran gcc-multilib  -y
RUN apt-get install gobjc++ aptitude libreadline-dev libbz2-dev libpcre2-dev libcurl4 libcurl4-openssl-dev -y
RUN apt-get install default-jre default-jdk openjdk-8-jdk openjdk-8-jre libssl-dev libxml2-dev -y 

RUN pip3 install awscli


RUN cd R-${R_VERSION} && ./configure     --prefix=/opt/R/${R_VERSION} --enable-memory-profiling --enable-R-shlib  --with-blas   --with-lapack --with-x=no
RUN cd /R-${R_VERSION} && make && make install
ENV PATH="/opt/R/${R_VERSION}/bin:${PATH}"
RUN rm -rf /R-${R_VERSION}
RUN rm -rf /R-${R_VERSION}.tar.gz

#RUN DEBIAN_FRONTEND="noninteractive" apt-get -y install tzdata

RUN R -e "install.packages('car', dependencies=TRUE, repos='https://cloud.r-project.org')"
RUN R -e "install.packages(c('optparse','data.table', 'ggplot2', 'ggpubr', 'ff', 'readxl', 'base64', 'parallel'),repos='https://cloud.r-project.org')" 
RUN R -e "install.packages('svglite',repos='https://cloud.r-project.org')"
RUN R -e "install.packages('gridExtra', repos='http://R-Forge.R-project.org')"

#RUN R -e "install.packages(c('BiocManager', repos='https://cloud.r-project.org'), repos='https://cloud.r-project.org')"
#RUN R -e "install.packages(c('bitops', 'RCurl', 'GenomeInfoDbData', 'matrixStats', 'GenomeInfoDb', 'XVector', 'MatrixGenerics'), repos='https://cloud.r-project.org')"
#RUN R -e "install.packages(c('DelayedArray', 'bit64', 'blob', 'memoise', 'plogr', 'IRanges', 'GenomicRanges', 'SummarizedExperiment'), repos='https://cloud.r-project.org')"
#RUN R -e "install.packages(c('Biostrings', 'S4Vectors', 'RSQLite', 'zlibbioc'), repos= 'https://cloud.r-project.org')"
#RUN R -e "install.packages(c('iterators', 'oligoClasses', 'preprocessCore', 'Biobase', 'BiocGenerics', 'affyio', 'illuminaio'), repos= 'https://cloud.r-project.org')"
#RUN R -e "install.packages(c('ellipse', 'mvtnorm', 'foreach', 'VGAM', 'limma', 'beanplot'), repos='https://cloud.r-project.org')"

#RUN R -e "BiocManager::install('crlmm')"

RUN apt-get install -y plink1.9
RUN ln -s /usr/bin/plink1.9   /usr/bin/plink
RUN apt-get install -y libfontconfig1-dev


#crlmm => bioconductor
