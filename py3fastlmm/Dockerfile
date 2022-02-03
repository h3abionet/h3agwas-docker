FROM quay.io/cybozu/ubuntu:20.04

RUN apt-get update && apt-get install -y locales && rm -rf /var/lib/apt/lists/* \
    && localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8
    ENV LANG en_US.utf8
ENV bolturl "https://storage.googleapis.com/broad-alkesgroup-public/BOLT-LMM/downloads/"
ENV bolversion "BOLT-LMM_v2.3.5"

RUN  apt-get update && apt-get install -y software-properties-common
RUN DEBIAN_FRONTEND="noninteractive" apt-get -y install tzdata
RUN add-apt-repository ppa:deadsnakes/ppa

RUN apt-get update && apt-get install -y plink1.9 wget gcc  wget  libpng-dev libopenblas-dev bash     libatlas-base-dev  unzip cmake libzstd-dev zlib1g zlib1g-dev  git make awscli build-essential  python3.6 python3.6-dev 
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
RUN wget https://raw.githubusercontent.com/h3abionet/h3agwas/master/utils/bin/gcta_1.93.2beta.zip && \
    unzip gcta_1.93.2beta.zip && \
    mv gcta_1.93.2beta/* /usr/local/bin/ && \
    rm -rf gcta_1.93.2beta*

RUN ln -s /usr/bin/plink1.9   /usr/bin/plink
RUN wget https://github.com/genetics-statistics/GEMMA/releases/download/v0.98.4/gemma-0.98.4-linux-static-AMD64.gz && gunzip gemma-0.98.4-linux-static-AMD64.gz && \
  mv gemma-0.98.4-linux-static-AMD64 /usr/local/bin/gemma && chmod +x /usr/local/bin/gemma


#
##RUN plink -h
##RUN gcta64 -h 
##RUN fastlmmc -h
#RUN gemma -h
#
