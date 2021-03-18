FROM centos:7
ENV url "http://cnsgenomics.com/software/gcta/gcta_1.92.2beta.zip"
ENV PYTHONNOUSERSITE 1 
# from a running Docker image I called `python -c "import sys; print(':'.join(x for x in sys.path if x))"`
#ENV PYTHONPATH /usr/lib64/python27.zip:/usr/lib64/python2.7:/usr/lib64/python2.7/plat-linux2:/usr/lib64/python2.7/lib-tk:/usr/lib64/python2.7/lib-old:/usr/lib64/python2.7/lib-dynload:/usr/lib64/python2.7/site-packages:/usr/lib64/python2.7/site-packages/gtk-2.0:/usr/lib/python2.7/site-packages
#ENV PYTHONPATH /usr/lib64/python27.zip:/usr/lib64/python2.7:/usr/lib64/python2.7/plat-linux2:/usr/lib64/python2.7/lib-tk:/usr/lib64/python2.7/lib-old:/usr/lib64/python2.7/lib-dynload:/usr/lib64/python2.7/site-packages:/usr/lib64/python2.7/site-packages/gtk-2.0:/usr/lib/python2.7/site-packages
#RUN yum install --assumeyes epel-release && yum update --assumeyes --skip-broken &&  yum install --assumeyes wget unzip 
RUN yum install --assumeyes epel-release && yum update --assumeyes --skip-broken &&  yum install --assumeyes wget gcc python3-devel wget freetype-devel libpng-devel openblas-devel bash python3-pip  sympy  atlas-devel gcc-c++ unzip cmake3 libzstd-devel zlib zlib-devel scl-utils centos-release-scl-rh git make awscli

RUN wget https://cnsgenomics.com/software/gcta/bin/gcta_1.93.2beta.zip && \
    unzip gcta_1.93.2beta.zip && \
    mv gcta_1.93.2beta/* /usr/local/bin/ && \
    rm -rf gcta_1.93.2beta*
