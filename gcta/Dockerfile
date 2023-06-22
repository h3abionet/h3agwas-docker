FROM quay.io/cybozu/ubuntu:20.04

ENV PYTHONNOUSERSITE 1 
# from a running Docker image I called `python -c "import sys; print(':'.join(x for x in sys.path if x))"`
#ENV PYTHONPATH /usr/lib64/python27.zip:/usr/lib64/python2.7:/usr/lib64/python2.7/plat-linux2:/usr/lib64/python2.7/lib-tk:/usr/lib64/python2.7/lib-old:/usr/lib64/python2.7/lib-dynload:/usr/lib64/python2.7/site-packages:/usr/lib64/python2.7/site-packages/gtk-2.0:/usr/lib/python2.7/site-packages
#ENV PYTHONPATH /usr/lib64/python27.zip:/usr/lib64/python2.7:/usr/lib64/python2.7/plat-linux2:/usr/lib64/python2.7/lib-tk:/usr/lib64/python2.7/lib-old:/usr/lib64/python2.7/lib-dynload:/usr/lib64/python2.7/site-packages:/usr/lib64/python2.7/site-packages/gtk-2.0:/usr/lib/python2.7/site-packages
ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Europe/Moscow
RUN apt update && apt-get install -y tzdata
RUN apt update &&  apt install -y wget gcc g++ unzip make zlib1g-dev vim default-jre python3-pip python3-pandas  
RUN pip3 install awscli


RUN apt-get install unzip && mkdir plink && cd plink && wget -c https://s3.amazonaws.com/plink1-assets/plink_linux_x86_64_20230116.zip && unzip plink_linux_x86_64_20230116.zip && cp plink /usr/bin/plink && cd ../ && rm -rf plink && chmod +x /usr/bin/plink
# py3fastlmm
RUN wget https://yanglab.westlake.edu.cn/software/gcta/bin/gcta-1.94.1-linux-kernel-3-x86_64.zip && \
    unzip gcta-1.94.1-linux-kernel-3-x86_64.zip && \
    cp gcta-1.94.1-linux-kernel-3-x86_64/gcta* /usr/local/bin/gcta64 && cp gcta-1.94.1-linux-kernel-3-x86_64/gcta* /usr/local/bin/gcta && \
    rm -rf gcta-1.94.1-linux-kernel-3-x86_64*
RUN pip3 install argparse numpy
#ENV PATH="/usr/lib/plink/:${PATH}"


#RUN gcta64 -h
#RUN plink -h
