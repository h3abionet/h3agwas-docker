FROM ubuntu:18.04
ENV PYTHONNOUSERSITE 1 
# from a running Docker image I called `python -c "import sys; print(':'.join(x for x in sys.path if x))"`
#ENV PYTHONPATH /usr/lib64/python27.zip:/usr/lib64/python2.7:/usr/lib64/python2.7/plat-linux2:/usr/lib64/python2.7/lib-tk:/usr/lib64/python2.7/lib-old:/usr/lib64/python2.7/lib-dynload:/usr/lib64/python2.7/site-packages:/usr/lib64/python2.7/site-packages/gtk-2.0:/usr/lib/python2.7/site-packages
#ENV PYTHONPATH /usr/lib64/python27.zip:/usr/lib64/python2.7:/usr/lib64/python2.7/plat-linux2:/usr/lib64/python2.7/lib-tk:/usr/lib64/python2.7/lib-old:/usr/lib64/python2.7/lib-dynload:/usr/lib64/python2.7/site-packages:/usr/lib64/python2.7/site-packages/gtk-2.0:/usr/lib/python2.7/site-packages
ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Europe/Moscow
RUN apt update && apt-get install -y tzdata
RUN apt update &&  apt install -y wget gcc g++ unzip make zlib1g-dev vim default-jre python3-pip python3-pandas  plink1.9 #zlib-dev


RUN wget https://raw.githubusercontent.com/h3abionet/h3agwas/master/utils/bin/gcta_1.93.2beta.zip && \
    unzip gcta_1.93.2beta.zip && \
    mv gcta_1.93.2beta/* /usr/local/bin/ && \
    rm -rf gcta_1.93.2beta*
RUN pip3 install argparse numpy
#ENV PATH="/usr/lib/plink/:${PATH}"
RUN ln -s /usr/bin/plink1.9   /usr/bin/plink

#RUN gcta64 -h
RUN plink -h
