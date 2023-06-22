FROM quay.io/cybozu/ubuntu:20.04

RUN apt-get update && apt-get install -y locales && rm -rf /var/lib/apt/lists/* \
    && localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8
    ENV LANG en_US.utf8

ENV bolturl "https://storage.googleapis.com/broad-alkesgroup-public/BOLT-LMM/downloads/"
ENV bolversion "BOLT-LMM_v2.3.6"

RUN  apt-get update && apt-get install -y software-properties-common
RUN DEBIAN_FRONTEND="noninteractive" apt-get -y install tzdata
RUN add-apt-repository ppa:deadsnakes/ppa

RUN apt-get update && apt-get install -y wget gcc  wget  libpng-dev libopenblas-dev bash     libatlas-base-dev  unzip cmake libzstd-dev zlib1g zlib1g-dev  git make awscli build-essential  python3.6 python3.6-dev 
RUN apt-get install -y apt-utils
RUN apt-get update && apt-get install -y python3-pip

ENV PYTHONPATH "/usr/lib64/python3.6/site-packages/:/usr/local/lib64/python3.6/site-packages/"
#RUN pip3 install --upgrade pip
RUN pip3 install --upgrade setuptools

RUN pip3 install sympy setuptools numpy scipy psutil wheel  matplotlib pandas scikit-learn sympy nose  numpy scipy psutil wheel 
RUN pip3 install awscli
#RUN python3 -m pip install fastlmm
#
RUN wget https://raw.githubusercontent.com/h3abionet/h3agwas/master/utils/bin/fastlmmc
RUN mv fastlmmc /usr/local/bin/
RUN chmod a+x /usr/local/bin/fastlmmc
#
RUN wget $bolturl""$bolversion".tar.gz" && tar zxvf   $bolversion".tar.gz" && \
         mv $bolversion/bolt $bolversion/tables  /usr/local/bin/ 
RUN mkdir /usr/local/bin/lib/ && mv $bolversion/lib/* /usr/local/bin/lib/

RUN chmod a+x /usr/local/bin/bolt
RUN wget https://yanglab.westlake.edu.cn/software/gcta/bin/gcta-1.94.1-linux-kernel-3-x86_64.zip && \
    unzip gcta-1.94.1-linux-kernel-3-x86_64.zip && \
    cp gcta-1.94.1-linux-kernel-3-x86_64/gcta* /usr/local/bin/gcta64 && cp gcta-1.94.1-linux-kernel-3-x86_64/gcta* /usr/local/bin/gcta && \
    rm -rf gcta-1.94.1-linux-kernel-3-x86_64*

RUN apt-get install unzip && mkdir plink && cd plink && wget -c https://s3.amazonaws.com/plink1-assets/plink_linux_x86_64_20230116.zip && unzip plink_linux_x86_64_20230116.zip && cp plink /usr/bin/plink && cd ../ && rm -rf plink && chmod +x /usr/bin/plink

RUN wget https://github.com/genetics-statistics/GEMMA/releases/download/v0.98.4/gemma-0.98.4-linux-static-AMD64.gz && gunzip gemma-0.98.4-linux-static-AMD64.gz && \
  mv gemma-0.98.4-linux-static-AMD64 /usr/local/bin/gemma && chmod +x /usr/local/bin/gemma


#
##RUN plink -h
##RUN gcta64 -h 
##RUN fastlmmc -h
#RUN gemma -h
#
