FROM quay.io/cybozu/ubuntu:20.04

ENV PYTHONNOUSERSITE 1

MAINTAINER JTB 

RUN apt-get update -qq
# install two helper packages we need
RUN apt install -y dirmngr apt-transport-https ca-certificates software-properties-common gnupg2  
RUN apt-get update && apt-get install -y apt-transport-https ca-certificates python3-pip python3-dev wget build-essential fort77 xorg-dev liblzma-dev libblas-dev gfortran gcc-multilib  
RUN apt-get install gobjc++ aptitude libreadline-dev libbz2-dev libpcre2-dev libcurl4 libcurl4-openssl-dev -y
RUN apt-get install default-jre default-jdk openjdk-8-jdk openjdk-8-jre libssl-dev libxml2-dev -y 
RUN apt-get install -y libx11-dev xserver-xorg-dev libxt-dev


RUN apt-get install xauth -y
RUN apt-get install libcairo2-dev libjpeg-dev libtiff-dev -y
ENV  R_VERSION 4.2.0
RUN curl -O https://cran.rstudio.com/src/base/R-4/R-${R_VERSION}.tar.gz && tar -xzvf R-${R_VERSION}.tar.gz
RUN cd R-${R_VERSION} && ./configure     --prefix=/opt/R/${R_VERSION}  \
  --enable-memory-profiling \
  --enable-R-shlib \
  --with-blas \
  --with-lapack
RUN cd /R-${R_VERSION} && make && make install
ENV PATH="/opt/R/${R_VERSION}/bin:${PATH}"
RUN rm -rf /R-${R_VERSION}
RUN rm -rf /R-${R_VERSION}.tar.gz

RUN pip3 install awscli
#RUN DEBIAN_FRONTEND="noninteractive" apt-get -y install tzdata

RUN R -e "install.packages('car', dependencies=TRUE, repos='https://cloud.r-project.org')"
RUN R -e "install.packages(c('optparse','data.table', 'ggplot2', 'ff', 'readxl', 'base64', 'parallel'),repos='https://cloud.r-project.org')" 
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
RUN apt-get update && apt-get install libcurl4-gnutls-dev -y
RUN apt-get install  libgl1-mesa-dev -y
RUN R -e "install.packages(\"devtools\", repos='cran.r-project.org/')"
RUN apt-get install  cmake -y
RUN R -e "devtools::install_github('kassambara/ggpubr')"
RUN R -e "install.packages(\"qqman\", repos='cran.r-project.org/')"

RUN pip3 install numpy scipy pandas matplotlib openpyxl biopython Distance 


#crlmm => bioconductor
