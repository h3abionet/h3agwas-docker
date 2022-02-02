FROM quay.io/cybozu/ubuntu:20.04

ENV PYTHONNOUSERSITE 1 
ENV gwamasrc "GWAMA_v2.2.2.zip"
ENV metalsrc "generic-metal-2011-03-25.tar.gz"
ENV bindir "/opt/bin"
ENV mrmegasrc "MR-MEGA_v0.1.5.zip"
ENV PATH=$bindir:$PATH
RUN mkdir -p $bindir
RUN apt update &&  apt install -y wget gcc g++ unzip make zlib1g-dev vim default-jre python3 python3-pip plink1.9 #zlib-dev 
RUN pip3 install awscli
## GWAMMA installation 
RUN mkdir /usr/local/src/gwama && wget http://www.geenivaramu.ee/tools/$gwamasrc && unzip $gwamasrc -d /usr/local/src/gwama/ && \
cd usr/local/src/gwama/ && make  && mv GWAMA $bindir/ && rm /$gwamasrc 
## Metal installation
RUN mkdir /usr/local/src/METAL && cd /usr/local/src/METAL && wget http://csg.sph.umich.edu/abecasis/metal/download/$metalsrc && tar -xzf $metalsrc  && cd generic-metal/ && make all && cp executables/metal $bindir/
## MR-MEGA installation
RUN mkdir /usr/local/src/MRMEGA/ && cd /usr/local/src/MRMEGA/ && wget http://www.geenivaramu.ee/tools/$mrmegasrc && unzip $mrmegasrc && make &&cp MR-MEGA $bindir/
RUN cd $bindir/ && wget https://raw.githubusercontent.com/h3abionet/h3agwas/master/utils/bin/Metasoft.zip && unzip  Metasoft.zip  
RUN pip3 install --upgrade pip
RUN pip3 install numpy scipy matplotlib pandas scikit-learn sympy nose 
RUN ln -s /usr/bin/plink1.9   /usr/bin/plink


