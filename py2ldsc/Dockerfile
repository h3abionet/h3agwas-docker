FROM quay.io/cybozu/ubuntu:20.04

# ENV bolturl "https://data.broadinstitute.org/alkesgroup/BOLT-LMM/downloads/BOLT-LMM_v2.3.2.tar.gz"
ENV PYTHONNOUSERSITE 1 
# from a running Docker image I called `python -c "import sys; print(':'.join(x for x in sys.path if x))"`
ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Europe/Moscow
RUN apt-get update && apt-get install -y software-properties-common && apt-add-repository universe
RUN apt-get update &&  apt-get install -y tzdata wget gcc g++ unzip make zlib1g-dev vim default-jre python2.7  python2-minimal build-essential git python2.7-dev plink1.9


RUN ln -s /usr/bin/python2.7 /usr/bin/python
RUN curl https://bootstrap.pypa.io/pip/2.7/get-pip.py -o get-pip.py
RUN python get-pip.py

RUN pip install --upgrade pip

RUN pip install scipy==0.18 
RUN pip install numpy==1.16 
RUN pip install pybedtools
RUN pip install nose==1.3
RUN pip install pandas==0.20
RUN pip install bitarray
#RUN ln -s /usr/include/locale.h /usr/include/xlocale.h
#RUN
RUN git clone https://github.com/bulik/ldsc.git && cd ldsc && mv * /usr/local/bin/
RUN ln -s /usr/bin/plink1.9   /usr/bin/plink

