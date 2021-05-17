FROM quay.io/cybozu/ubuntu:20.04

ENV PYTHONNOUSERSITE 1 


RUN apt-get update 
RUN DEBIAN_FRONTEND="noninteractive" apt-get -y install tzdata
RUN apt-get install -y software-properties-common && apt-add-repository universe
RUN apt-get update &&  apt install -y wget build-essential unzip make zlib1g-dev vim default-jre python2.7 python-pip  plink1.9 #zlib-dev

ENV bolturl "https://storage.googleapis.com/broad-alkesgroup-public/BOLT-LMM/downloads/"
ENV bolversion "BOLT-LMM_v2.3.5"

RUN wget $bolturl""$bolversion".tar.gz" && tar zxvf   $bolversion".tar.gz" && \
         mv $bolversion/bolt $bolversion/tables /usr/local/bin/ && chmod a+x /usr/local/bin/bolt


RUN pip install --upgrade pip
RUN DEBIAN_FRONTEND="noninteractive" apt-get -y install tzdata
RUN apt-get install -y python-pandas

RUN pip install setuptools
RUN pip install numpy 
RUN pip install scipy 
RUN pip install matplotlib 
RUN pip install pandas 
RUN pip install scikit-learn 
RUN pip install nose 

RUN apt-get install -y python-sympy
RUN pip install sympy

RUN wget https://raw.githubusercontent.com/h3abionet/h3agwas/master/utils/bin/fastlmmc
RUN mv fastlmmc /usr/local/bin/
RUN chmod a+x /usr/local/bin/fastlmmc


RUN wget https://raw.githubusercontent.com/h3abionet/h3agwas/master/utils/bin/gcta_1.93.2beta.zip && \
    unzip gcta_1.93.2beta.zip && \
    mv gcta_1.93.2beta/* /usr/local/bin/ && \
    rm -rf gcta_1.93.2beta*

RUN wget https://github.com/genetics-statistics/GEMMA/releases/download/v0.98.4/gemma-0.98.4-linux-static-AMD64.gz && gunzip gemma-0.98.4-linux-static-AMD64.gz && \
  mv gemma-0.98.4-linux-static-AMD64 /usr/local/bin/gemma && chmod +x /usr/local/bin/gemma


#ENV PATH="/usr/lib/plink/:${PATH}"
RUN ln -s /usr/bin/plink1.9   /usr/bin/plink
#RUN plink -h
#RUN gcta64 -h

