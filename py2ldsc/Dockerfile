FROM quay.io/cybozu/ubuntu:20.04

# ENV bolturl "https://data.broadinstitute.org/alkesgroup/BOLT-LMM/downloads/BOLT-LMM_v2.3.2.tar.gz"
ENV PYTHONNOUSERSITE 1 
# from a running Docker image I called `python -c "import sys; print(':'.join(x for x in sys.path if x))"`
ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Europe/Moscow
RUN apt update && apt-get install -y tzdata
RUN apt-get install -y software-properties-common apt-add-repository universe
RUN apt update &&  apt install -y wget gcc g++ unzip make zlib1g-dev vim default-jre python2.7 python-pip  python-pandas #zlib-dev

RUN pip install scipy==0.18 
RUN pip install numpy==1.16 
RUN pip install pybedtools==0.7 
RUN pip install nose==1.3
RUN pip install pandas==0.20
RUN pip install bitarray==0.8
RUN apt install -y git 
#RUN ln -s /usr/include/locale.h /usr/include/xlocale.h
#RUN
RUN git clone https://github.com/bulik/ldsc.git && cd ldsc && mv * /usr/local/bin/

