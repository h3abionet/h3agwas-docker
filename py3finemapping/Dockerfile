FROM quay.io/cybozu/ubuntu:20.04

RUN apt-get update && apt-get install -y locales && rm -rf /var/lib/apt/lists/* \
    && localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8
    ENV LANG en_US.utf8


ENV bolturl "https://storage.googleapis.com/broad-alkesgroup-public/BOLT-LMM/downloads/"
ENV bolversion "BOLT-LMM_v2.3.6"


RUN  apt-get update && apt-get install -y software-properties-common
RUN DEBIAN_FRONTEND="noninteractive" apt-get -y install tzdata
RUN add-apt-repository ppa:deadsnakes/ppa

RUN apt-get update && apt-get install -y plink1.9 wget gcc  wget  libpng-dev libopenblas-dev bash     libatlas-base-dev  unzip cmake libzstd-dev zlib1g zlib1g-dev  git make awscli build-essential  python3.6 python3.6-dev 
RUN apt-get install -y apt-utils
RUN apt-get update && apt-get install -y python3-pip

ENV PYTHONPATH "/usr/lib64/python3.6/site-packages/:/usr/local/lib64/python3.6/site-packages/"

RUN ln -s /usr/bin/plink1.9   /usr/bin/plink

RUN wget https://github.com/gkichaev/PAINTOR_V3.0/archive/refs/tags/3.0.zip && unzip 3.0.zip && cd PAINTOR_V3.0-3.0 &&  bash install.sh
RUN mv /PAINTOR_V3.0-3.0/PAINTOR /usr/bin/ && chmod +x /usr/bin/PAINTOR 

RUN wget http://www.christianbenner.com/finemap_v1.4_x86_64.tgz && tar -xzf finemap_v1.4_x86_64.tgz
RUN mv /finemap_v1.4_x86_64/finemap_v1.4_x86_64 /usr/bin/finemap && chmod +x /usr/bin/finemap
RUN git clone https://bitbucket.org/Wenan/caviarbf/ && cd caviarbf && make && mv caviarbf model_search  /usr/bin/

#
##RUN plink -h
##RUN gcta64 -h 
##RUN fastlmmc -h
#RUN gemma -h
#
