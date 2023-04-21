FROM quay.io/cybozu/ubuntu:20.04
ENV PYTHONNOUSERSITE 1  
RUN apt-get -y update && apt-get -y install build-essential python3-dev python3 python3-pip gfortran wget libpng-dev libopenblas-dev 

RUN apt-get install -y curl  vcftools bcftools tabix samtools git vim libblas-dev
RUN apt-get install libgsl-dev libblas-dev liblapack-dev liblapacke-dev libbz2-dev -y 
RUN apt-get install liblzma-dev -y 
RUN pip3 install numpy scipy pandas matplotlib openpyxl biopython Distance CrossMap awscli


RUN git clone https://github.com/gavinband/qctool && cd qctool
RUN apt-get install -y zlib1g libboost-all-dev sqlite3

RUN wget -c https://www.well.ox.ac.uk/~gav/resources/qctool_v2.0.6-Ubuntu16.04-x86_64.tgz && tar -xzf qctool_v2.0.6-Ubuntu16.04-x86_64.tgz
RUN mv qctool_v2.0.6-Ubuntu16.04-x86_64/qctool  /usr/bin/ && chmod +x /usr/bin/qctool
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


RUN  git clone https://github.com/DReichLab/EIG/ && cd /EIG//src make LDLIBS="-llapacke" &&  make install LDLIBS="-llapacke" && mv ../bin/* /usr/bin/  &&  cd / && rm -rf EIG

RUN  wget http://code.enkre.net/bgen/tarball/release/bgen.tgz && tar -xzf bgen.tgz && cd bgen.tgz/ && ./waf configure && ./waf && cp build/apps/bgenix /usr/bin/
RUN apt-get install unzip libterm-readkey-perl -y
RUN mkdir tmpbin && cd tmpbin && wget http://www.well.ox.ac.uk/~wrayner/tools/HRC-1000G-check-bim-v4.2.7.zip && unzip HRC-1000G-check-bim-v4.2.7.zip && cp HRC-1000G-check-bim.pl /usr/bin/ && chmod +x /usr/bin/HRC-1000G-check-bim.pl && cd ../ && rm -rf tmpbin
RUN apt-get install perl libarchive-zip-perl libdbi-perl -y
#RUN git clone https://github.com/Ensembl/ensembl-vep.git && cd ensembl-vep && perl ./INSTALL.pl
ENV TOOLS=/usr/bin/
ENV TOOL_NAME=annovar
ENV TOOL_VERSION=current
ENV TARBALL_LOCATION=http://www.openbioinformatics.org/annovar/download/0wgxR2rIVP/
ENV TARBALL=annovar.latest.tar.gz
ENV TARBALL_FOLDER=$TOOL_NAME
ENV DEST=$TOOLS/$TOOL_NAME/$TOOL_VERSION
ENV PATH=$TOOLS/$TOOL_NAME/$TOOL_VERSION/bin:$PATH


# INSTALL
RUN wget $TARBALL_LOCATION/$TARBALL ; \
    tar xf $TARBALL --wildcards *pl ; \
    rm -rf $TARBALL ; \
    cd $TARBALL_FOLDER ; \
    mkdir -p $TOOLS/$TOOL_NAME/$TOOL_VERSION/bin ; \
    cp *pl $TOOLS/$TOOL_NAME/$TOOL_VERSION/bin/ -R ; \
    mkdir /databases ; \
    ln -s /databases/ $TOOLS/$TOOL_NAME/$TOOL_VERSION/bin/humandb ; \
    cd ../ ; \
    rm -rf $TARBALL_FOLDER ;


RUN apt-get install unzip && mkdir plink && cd plink && wget -c https://s3.amazonaws.com/plink1-assets/plink_linux_x86_64_20230116.zip && unzip plink_linux_x86_64_20230116.zip && cp plink /usr/bin/plink && cd ../ && rm -rf plink && chmod +x /usr/bin/plink

