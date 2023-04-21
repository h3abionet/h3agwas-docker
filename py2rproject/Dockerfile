FROM quay.io/cybozu/ubuntu:20.04

ENV PYTHONNOUSERSITE 1

MAINTAINER JTB 

RUN apt-get update -qq
# install two helper packages we need
RUN apt install -y dirmngr apt-transport-https ca-certificates software-properties-common gnupg2 
RUN apt-get update && apt-get install -y apt-transport-https ca-certificates wget 
RUN apt-get update && apt-get install -y python2.7  python2-minimal python2.7-dev tabix git
# import the signing key (by Michael Rutter) for these repo
#RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9
# add the R 3.6 repo from CRAN -- adjust 'focal' to 'groovy' or 'bionic' as needed
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9

RUN add-apt-repository "deb https://cloud.r-project.org/bin/linux/ubuntu $(lsb_release -sc)-cran40/"
RUN DEBIAN_FRONTEND="noninteractive" apt-get -y install tzdata
RUN apt-get update -y && \
    apt-get install r-base-core -y && \
    apt-get install r-cran-kernsmooth -y

#RUN apt-get install -y libcurl4-openssl-dev
#RUN apt-get install -y libssl-dev libxml2-dev
#RUN R -e "install.packages('car', dependencies=TRUE, repos='https://cloud.r-project.org')"
#RUN R -e "install.packages(c('optparse','data.table', 'ggplot2','gridExtra'),repos='https://cloud.r-project.org')" 
#RUN R -e "install.packages('BiocManager', repos='https://cloud.r-project.org');BiocManager::install('crlmm')"
#RUN R -e "install.packages('svglite')"

RUN R -e "install.packages(c('gridExtra', 'ggplot2'))"

RUN apt-get install unzip && mkdir plink && cd plink && wget -c https://s3.amazonaws.com/plink1-assets/plink_linux_x86_64_20230116.zip && unzip plink_linux_x86_64_20230116.zip && cp plink /usr/bin/plink && cd ../ && rm -rf plink && chmod +x /usr/bin/plink

RUN apt-get install -y libfontconfig1-dev
RUN ln -s /usr/bin/python2.7 /usr/bin/python

RUN curl https://bootstrap.pypa.io/pip/2.7/get-pip.py -o get-pip.py
RUN python get-pip.py

RUN pip install awscli
