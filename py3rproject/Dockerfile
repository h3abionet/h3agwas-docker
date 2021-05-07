FROM ubuntu:18.04

MAINTAINER Eugene de Beste

RUN apt update -qq
# install two helper packages we need
RUN apt install -y dirmngr apt-transport-https ca-certificates software-properties-common gnupg2
RUN apt-get install -y apt-transport-https ca-certificates python3-pip python3-dev 
# import the signing key (by Michael Rutter) for these repo
#RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9
# add the R 3.6 repo from CRAN -- adjust 'focal' to 'groovy' or 'bionic' as needed
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9

RUN add-apt-repository "deb https://cloud.r-project.org/bin/linux/ubuntu $(lsb_release -sc)-cran40/"
RUN DEBIAN_FRONTEND="noninteractive" apt-get -y install tzdata
RUN apt-get update -y && \
    apt-get install r-base-core -y && \
    apt-get install r-cran-kernsmooth -y

RUN apt-get install -y libcurl4-openssl-dev
RUN apt-get install -y libssl-dev libxml2-dev
RUN R -e "install.packages('car', dependencies=TRUE, repos='https://cloud.r-project.org')"
RUN R -e "install.packages(c('optparse','data.table', 'ggplot2', 'ggpubr', 'ff', 'readxl', 'base64'),repos='https://cloud.r-project.org')" 
RUN R -e  "install.packages('BiocManager', repos='https://cloud.r-project.org');BiocManager::install('crlmm')"
#crlmm => bioconductor