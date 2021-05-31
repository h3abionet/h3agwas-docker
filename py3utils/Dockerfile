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
#RUN apt-get install
