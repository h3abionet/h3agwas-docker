FROM quay.io/cybozu/ubuntu:20.04
ENV PYTHONNOUSERSITE 1  
RUN apt-get -y update && apt-get -y install build-essential python3-dev python3 python3-pip gfortran wget libpng-dev libopenblas-dev plink1.9 
#RUN ln -s /usr/include/locale.h /usr/include/xlocale.h
RUN pip3 install numpy scipy pandas matplotlib openpyxl biopython Distance CrossMap awscli
RUN apt-get install -y curl  vcftools bcftools tabix samtools
######ENV PATH="/usr/lib/plink/:${PATH}"
RUN ln -s /usr/bin/plink1.9   /usr/bin/plink

