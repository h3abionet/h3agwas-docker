FROM quay.io/cybozu/ubuntu:20.04

ENV PYTHONNOUSERSITE 1 


RUN apt-get update 
RUN DEBIAN_FRONTEND="noninteractive" apt-get -y install tzdata
RUN apt-get install -y software-properties-common && apt-add-repository universe 
RUN apt-get update &&  apt install -y wget build-essential unzip make zlib1g-dev vim default-jre python2.7  plink1.9 #zlib-dev curl 

ENV bolturl "https://storage.googleapis.com/broad-alkesgroup-public/BOLT-LMM/downloads/"
ENV bolversion "BOLT-LMM_v2.3.5"

RUN ln -s /usr/bin/python2.7 /usr/bin/python
RUN apt-get install -y python2.7 python2-minimal #python-pandas
RUN curl https://bootstrap.pypa.io/pip/2.7/get-pip.py -o get-pip.py
RUN python get-pip.py
#
#
#
RUN pip install --upgrade pip
#
RUN pip install setuptools
RUN pip install numpy 
RUN pip install scipy 
RUN pip install matplotlib 
RUN pip install pandas 
RUN pip install scikit-learn 
RUN pip install nose 
RUN pip install panda
RUN pip install sympy
#
RUN wget https://raw.githubusercontent.com/h3abionet/h3agwas/master/utils/bin/fastlmmc
RUN mv fastlmmc /usr/local/bin/
RUN chmod a+x /usr/local/bin/fastlmmc
RUN ln -s /usr/bin/plink1.9   /usr/bin/plink

#
#
RUN wget https://raw.githubusercontent.com/h3abionet/h3agwas/master/utils/bin/gcta_1.93.2beta.zip && \
    unzip gcta_1.93.2beta.zip && \
    mv gcta_1.93.2beta/* /usr/local/bin/ && \
    rm -rf gcta_1.93.2beta*
#
RUN wget $bolturl""$bolversion".tar.gz" && tar zxvf   $bolversion".tar.gz" && \
         mv $bolversion/bolt $bolversion/tables  /usr/local/bin/
RUN chmod a+x /usr/local/bin/bolt

RUN mkdir /usr/local/bin/lib/ && mv $bolversion/lib/* /usr/local/bin/lib/

RUN wget https://github.com/genetics-statistics/GEMMA/releases/download/v0.98.4/gemma-0.98.4-linux-static-AMD64.gz && gunzip gemma-0.98.4-linux-static-AMD64.gz && \
  mv gemma-0.98.4-linux-static-AMD64 /usr/local/bin/gemma && chmod +x /usr/local/bin/gemma

