FROM quay.io/cybozu/ubuntu:20.04
ENV PYTHONNOUSERSITE 1  
RUN apt-get -y update && apt-get -y install build-essential python3-dev python3 python3-pip gfortran wget libpng-dev libopenblas-dev plink1.9 
#RUN ln -s /usr/include/locale.h /usr/include/xlocale.h
RUN pip3 install numpy scipy pandas matplotlib openpyxl biopython Distance CrossMap awscli
RUN apt-get install -y curl  vcftools bcftools tabix samtools git vim libblas-dev
######ENV PATH="/usr/lib/plink/:${PATH}"
RUN ln -s /usr/bin/plink1.9   /usr/bin/plink

RUN git clone https://github.com/gavinband/qctool && cd qctool
RUN apt-get install -y zlib1g libboost-all-dev sqlite3
#RUN cd qctool && python3 ./waf configure 
#RUN cd qctool && python3 ./waf
RUN wget -c https://www.well.ox.ac.uk/~gav/resources/qctool_v2.0.6-Ubuntu16.04-x86_64.tgz && tar -xzf qctool_v2.0.6-Ubuntu16.04-x86_64.tgz
RUN mv qctool_v2.0.6-Ubuntu16.04-x86_64/qctool  /usr/bin/
RUN apt-get -y update && apt-get -y install python2.7 python2-minimal
RUN ln -s /usr/bin/python2.7 /usr/bin/python
RUN curl https://bootstrap.pypa.io/pip/2.7/get-pip.py -o get-pip.py
RUN python get-pip.py

RUN pip install setuptools
RUN pip install numpy
RUN pip install scipy
RUN pip install matplotlib
RUN pip install pandas
RUN pip install scikit-learn
RUN pip install nose
RUN pip install panda
RUN pip install sympy


RUN wget -c  https://github.com/DReichLab/EIG/archive/v7.2.1.tar.gz
RUN apt-get install libgsl-dev libblas-dev liblapack-dev liblapacke-dev -y 
RUN tar -xzf v7.2.1.tar.gz
RUN cd /EIG-7.2.1/src/ && make LDLIBS="-llapacke" &&  make install LDLIBS="-llapacke" && mv ../bin/* /usr/bin/ 



