FROM quay.io/cybozu/ubuntu:20.04
## adapted from https://github.com/weizhouUMICH/Docker/blob/master/SAIGE/Dockerfile

LABEL maintainer="wzhou@broadinstitute.org"

ENV LC_ALL C.UTF-8
ENV LANG C.UTF-8

RUN apt-get update && \
    apt-get install curl vim bcftools vcftools make gcc g++ cmake gfortran libreadline-dev \
    libz-dev libbz2-dev liblzma-dev libpcre3-dev libssl-dev libcurl4-openssl-dev \
    libopenblas-dev default-jre unzip libboost-all-dev \
    libpng-dev libcairo2-dev tabix --yes && \
    apt-get clean && \
    curl -O https://cloud.r-project.org/src/base/R-3/R-3.5.1.tar.gz && \
    tar xvzf R-3.5.1.tar.gz && \
    cd R-3.5.1 && \
    ./configure --with-x=no --with-blas="-lopenblas" && \
    make && \
    mkdir -p /usr/local/lib/R/lib && \
    make install && \
    cd .. && \
    rm -rf R-3.5.1*

RUN apt-get install python3-pip --yes && \
    pip3 install cget

RUN apt install wget
#RUN src_branch=master  && \
#	repo_src_url=https://github.com/weizhouUMICH/SAIGE && \
#	git clone --depth 0 -b $src_branch $repo_src_url


#RUN wget https://github.com/weizhouUMICH/SAIGE/archive/master.zip && \
#        unzip master.zip && \
#        mv SAIGE-master SAIGE 
RUN apt-get update

RUN apt-get install -y libxml2-dev

RUN echo "update 0.36.4 hello" &&  wget https://github.com/weizhouUMICH/SAIGE/archive/master.zip && \
	unzip master.zip && \
	mv SAIGE-master SAIGE
RUN echo "update3"

#RUN Rscript SAIGE/extdata/install_packages.R
RUN cp SAIGE/extdata/install_packages.R /usr/local/bin/


RUN Rscript /usr/local/bin/install_packages.R


RUN Rscript -e 'devtools::install_github("leeshawn/SKAT")'

RUN echo "update 0.36.6" &&  wget https://github.com/weizhouUMICH/SAIGE/archive/master.zip && \
        unzip master.zip && \
        mv SAIGE-master SAIGE

RUN R CMD INSTALL SAIGE
RUN echo "hello world4" 

RUN Rscript SAIGE/extdata/step1_fitNULLGLMM.R --help

RUN Rscript SAIGE/extdata/step2_SPAtests.R --help



RUN cp SAIGE/extdata/step1_fitNULLGLMM.R SAIGE/extdata/step2_SPAtests.R SAIGE/extdata/createSparseGRM.R /usr/local/bin/

RUN chmod +x /usr/local/bin/*.R

ENV PATH "/usr/local/bin/:$PATH"

RUN Rscript /usr/local/bin/createSparseGRM.R  --help

RUN Rscript /usr/local/bin/step1_fitNULLGLMM.R --help

RUN Rscript /usr/local/bin/step2_SPAtests.R --help


#RUN rm -r SAIGE
