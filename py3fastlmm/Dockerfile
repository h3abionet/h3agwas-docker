FROM ubuntu:18.04
#ENV plinksrc "plink_linux_x86_64_20190617.zip"
#ENV bolturl "https://data.broadinstitute.org/alkesgroup/BOLT-LMM/downloads/BOLT-LMM_v2.3.2.tar.gz"
RUN apt-get update && apt-get install -y locales && rm -rf /var/lib/apt/lists/* \
    && localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8
    ENV LANG en_US.utf8
ENV bolturl "https://storage.googleapis.com/broad-alkesgroup-public/BOLT-LMM/downloads/"
ENV bolversion "BOLT-LMM_v2.3.5"
ENV PYTHONNOUSERSITE 1 
#RUN yum install --assumeyes epel-release && yum update --assumeyes --skip-broken &&  yum install --assumeyes wget gcc python3-devel wget freetype-devel libpng-devel openblas-devel bash python3-pip  sympy  atlas-devel gcc-c++ unzip cmake3 libzstd-devel zlib zlib-devel scl-utils centos-release-scl-rh git make awscli

RUN  apt-get update && apt-get install -y software-properties-common
RUN DEBIAN_FRONTEND="noninteractive" apt-get -y install tzdata
RUN add-apt-repository ppa:deadsnakes/ppa

RUN apt-get update && apt-get install -y plink1.9 wget gcc  wget  libpng-dev libopenblas-dev bash     libatlas-base-dev  unzip cmake libzstd-dev zlib1g zlib1g-dev  git make awscli build-essential  python3.6 python3.6-dev 
RUN apt-get install -y apt-utils
RUN apt-get update && apt-get install -y python3-pip

#RUN yum -y install  devtoolset-8
#RUN ln -s /usr/bin/cmake3 /usr/local/bin/cmake && ln -s /usr/bin/ctest3 /usr/local/bin/ctest
#RUN git clone https://github.com/horta/almosthere && cd almosthere && mkdir build && cd build && cmake .. -DCMAKE_BUILD_TYPE=Release -DBUILD_SHARED_LIBS=ON &&  make && make test && make install
# We need a version of gcc  > the default so we enable devtoolset which gives us gcc-8
# that's what scl enable does 
#RUN scl enable devtoolset-8 "curl -fsSL https://git.io/JerYI | GITHUB_USER=limix GITHUB_PROJECT=bgen bash"
#RUN scl enable devtoolset-8 "python3 -m pip install bgen-reader"
ENV PYTHONPATH "/usr/lib64/python3.6/site-packages/:/usr/local/lib64/python3.6/site-packages/"
#RUN pip3 install --upgrade pip
RUN pip3 install --upgrade setuptools

RUN pip3 install sympy setuptools numpy scipy psutil wheel  matplotlib pandas scikit-learn sympy nose  numpy scipy psutil wheel 
#RUN python3 -m pip install fastlmm
#
RUN wget https://raw.githubusercontent.com/h3abionet/h3agwas/master/utils/bin/fastlmmc
RUN mv fastlmmc /usr/local/bin/
RUN chmod a+x /usr/local/bin/fastlmmc

#RUN wget http://s3.amazonaws.com/plink1-assets/$plinksrc && unzip $plinksrc -d /usr/local/bin/ && \
#rm $plinksrc /usr/local/bin/toy.ped /usr/local/bin/toy.map /usr/local/bin/LICENSE && \
#chmod a+x /usr/local/bin/plink
##https://storage.googleapis.com/broad-alkesgroup-public/BOLT-LMM/downloads/BOLT-LMM_v2.3.5.tar.gz
RUN wget $bolturl""$bolversion".tar.gz" && tar zxvf   $bolversion".tar.gz" && \
         mv $bolversion/bolt $bolversion/tables /usr/local/bin/ && chmod a+x /usr/local/bin/bolt
RUN wget https://raw.githubusercontent.com/h3abionet/h3agwas/master/utils/bin/gcta_1.93.2beta.zip && \
    unzip gcta_1.93.2beta.zip && \
    mv gcta_1.93.2beta/* /usr/local/bin/ && \
    rm -rf gcta_1.93.2beta*

RUN wget https://github.com/genetics-statistics/GEMMA/releases/download/v0.98.4/gemma-0.98.4-linux-static-AMD64.gz && gunzip gemma-0.98.4-linux-static-AMD64.gz && \
  mv gemma-0.98.4-linux-static-AMD64 /usr/local/bin/gemma && chmod +x /usr/local/bin/gemma


#ENV PATH="/usr/lib/plink/:${PATH}"
ENV ln -s /usr/bin/plink1.9   /usr/bin/plink

#RUN plink -h
#RUN gcta64 -h 
#RUN fastlmmc -h
RUN gemma -h

