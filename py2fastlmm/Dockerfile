FROM ubuntu:18.04
ENV plinksrc "plink_linux_x86_64_20190617.zip"
# ENV bolturl "https://data.broadinstitute.org/alkesgroup/BOLT-LMM/downloads/BOLT-LMM_v2.3.2.tar.gz"
ENV bolturl "https://data.broadinstitute.org/alkesgroup/BOLT-LMM/downloads/old/BOLT-LMM_v2.3.2.tar.gz"
ENV PYTHONNOUSERSITE 1 
# from a running Docker image I called `python -c "import sys; print(':'.join(x for x in sys.path if x))"`
ENV PYTHONPATH /usr/lib64/python27.zip:/usr/lib64/python2.7:/usr/lib64/python2.7/plat-linux2:/usr/lib64/python2.7/lib-tk:/usr/lib64/python2.7/lib-old:/usr/lib64/python2.7/lib-dynload:/usr/lib64/python2.7/site-packages:/usr/lib64/python2.7/site-packages/gtk-2.0:/usr/lib/python2.7/site-packages
#RUN apt update && apt install wget gcc gfortran python3 python-dev py-pip build-base wget freetype-dev libpng-dev openblas-dev bash python-pip numpy scipy python-matplotlib ipython python-pandas sympy python-nose atlas-devel gcc-c++ unzip
RUN apt update &&  apt install -y wget gcc g++ unzip make zlib1g-dev vim default-jre python2.7 python-pip  #zlib-dev

#RUN ln -s /usr/include/locale.h /usr/include/xlocale.h
RUN wget http://s3.amazonaws.com/plink1-assets/$plinksrc && unzip $plinksrc -d /usr/local/bin/ && \
rm $plinksrc /usr/local/bin/toy.ped /usr/local/bin/toy.map /usr/local/bin/LICENSE && \
chmod a+x /usr/local/bin/plink
RUN wget $bolturl && tar zxvf BOLT-LMM_v2.3.2.tar.gz && \
mv BOLT-LMM_v2.3.2/bolt BOLT-LMM_v2.3.2/tables /usr/local/bin/ && chmod a+x /usr/local/bin/bolt
#RUN pip install --upgrade pip
    #chmod a+x /usr/lib64/python2.7/site-packages/fastlmm/association/Fastlmm_autoselect/fastlmmc && \
    #ln -s /usr/lib64/python2.7/site-packages/fastlmm/association/Fastlmm_autoselect/fastlmmc /usr/local/bin/
#RUN pip install --upgrade pip
#RUN pip install setuptools
#RUN pip install numpy 
#RUN pip install scipy 
#RUN pip install matplotlib 
#RUN pip install pandas 
#RUN pip install scikit-learn 
#RUN pip install nose 
#RUN pip install sympy

#RUN pip install pip install fastlmm && \
#    chmod a+x /usr/lib64/python2.7/site-packages/fastlmm/association/Fastlmm_autoselect/fastlmmc && \
#    ln -s /usr/lib64/python2.7/site-packages/fastlmm/association/Fastlmm_autoselect/fastlmmc /usr/local/bin/


