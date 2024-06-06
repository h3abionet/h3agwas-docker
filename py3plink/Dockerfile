FROM quay.io/cybozu/ubuntu:20.04
ENV PYTHONNOUSERSITE 1  
#RUN apk --no-cache --update-cache add gcc gfortran python3 python3-dev py3-pip build-base wget freetype-dev libpng-dev openblas-dev bash
RUN apt-get -y update && apt-get -y install build-essential python3-dev python3 python3-pip gfortran wget libpng-dev libopenblas-dev  ca-certificates
#RUN ln -s /usr/include/locale.h /usr/include/xlocale.h
RUN pip3 install numpy scipy pandas==2.0.0 matplotlib openpyxl biopython Distance
RUN pip3 install awscli
RUN apt-get install -y curl 
RUN wget https://github.com/genetics-statistics/GEMMA/releases/download/v0.98.5/gemma-0.98.5-linux-static-AMD64.gz && gunzip gemma-0.98.5-linux-static-AMD64.gz && \
  mv gemma-0.98.5-linux-static-AMD64 /usr/local/bin/gemma && chmod +x /usr/local/bin/gemma
#RUN wget https://biogems.info/download/gemma-0.98.6-pre1.gz && gunzip gemma-0.98.6-pre1.gz &&  mv gemma-0.98.6-pre1 /usr/local/bin/gemma-0.98.6 && chmod +x /usr/local/bin/gemma-0.98.6
######ENV PATH="/usr/lib/plink/:${PATH}"
RUN apt-get install unzip
RUN mkdir plink && cd plink && wget -c https://s3.amazonaws.com/plink1-assets/plink_linux_x86_64_20230116.zip && unzip plink_linux_x86_64_20230116.zip && cp plink /usr/bin/plink && cd ../ && rm -rf plink && chmod +x /usr/bin/plink

RUN wget https://raw.githubusercontent.com/h3abionet/h3agwas/master/utils/bin/fastlmmc
RUN mv fastlmmc /usr/local/bin/
RUN chmod a+x /usr/local/bin/fastlmmc

#RUN plink -h
#RUN gemma -h
#RUN gemma-0.98.6 -h

RUN pip install -U Jinja2


#RUN WGET HTTP://S3.AMAZONAWS.COM/PLINK1-ASSETS/$PLINKSRC && UNZIP $PLINKSRC -D /USR/LOCAL/BIN/ && \

#    RM $PLINKSRC /USR/LOCAL/BIN/TOY.PED /USR/LOCAL/BIN/TOY.MAP /USR/LOCAL/BIN/LICENSE && \
#    CHMOD A+X /USR/LOCAL/BIN/PLINK
#RUN WGET $GEMMAURL && GUNZIP GEMMA-$GEMMAVER-LINUX-STATIC-AMD64.GZ && \
#    MV GEMMA-$GEMMAVER-LINUX-STATIC-AMD64 /USR/LOCAL/BIN/GEMMA && CHMOD +X /USR/LOCAL/BIN/GEMMA
#ENV PYTHONPATH ""
#RUN wget http://code.enkre.net/bgen/tarball/release/bgen.tgz & tar -& cd bgen & ./waf configure & ./waf
RUN wget https://github.com/rgcgithub/regenie/releases/download/v3.1.3/regenie_v3.1.3.gz_x86_64_Linux.zip && unzip regenie_v3.1.3.gz_x86_64_Linux.zip && mv regenie_v3.1.3.gz_x86_64_Linux /usr/local/bin/regenie  && chmod +x /usr/local/bin/regenie

RUN wget https://raw.githubusercontent.com/isglobal-brge/imputeInversion/master/HRC-1000G-check-bim.pl && mv HRC-1000G-check-bim.pl /usr/local/bin/ && chmod +x /usr/local/bin/HRC-1000G-check-bim.pl
RUN cpan Term::ReadKey
