FROM ubuntu:latest

MAINTAINER Eugene de Beste

RUN apt update -qq
# install two helper packages we need
RUN apt install -y --no-install-recommends software-properties-common dirmngr
# import the signing key (by Michael Rutter) for these repo
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9
# add the R 4.0 repo from CRAN -- adjust 'focal' to 'groovy' or 'bionic' as needed
RUN apt-get install -y apt-transport-https ca-certificates python3-pip python3-devel 
RUN add-apt-repository "deb https://cloud.r-project.org/bin/linux/ubuntu $(lsb_release -sc)-cran40/"
RUN apt-get update -y && \
    apt-get install r-base-core -y && \
    apt-get install r-cran-kernsmooth -y

RUN R -e "install.packages(c('optparse','data.table', 'ggplot2'),repos='https://cloud.r-project.org')" 
