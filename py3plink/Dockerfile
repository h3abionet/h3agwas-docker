FROM quay.io/cybozu/ubuntu:20:04
ENV PYTHONNOUSERSITE 1  
#RUN apk --no-cache --update-cache add gcc gfortran python3 python3-dev py3-pip build-base wget freetype-dev libpng-dev openblas-dev bash
RUN apt-get -y update && apt-get -y install build-essential python3-dev python3 python3-pip gfortran wget libpng-dev libopenblas-dev plink1.9
#RUN ln -s /usr/include/locale.h /usr/include/xlocale.h
RUN pip3 install numpy scipy pandas matplotlib openpyxl biopython Distance
RUN pip3 install awscli
RUN apt-get install -y curl 
RUN wget https://github.com/genetics-statistics/GEMMA/releases/download/v0.98.4/gemma-0.98.4-linux-static-AMD64.gz && gunzip gemma-0.98.4-linux-static-AMD64.gz && \
  mv gemma-0.98.4-linux-static-AMD64 /usr/local/bin/gemma && chmod +x /usr/local/bin/gemma
######ENV PATH="/usr/lib/plink/:${PATH}"
RUN ln -s /usr/bin/plink1.9   /usr/bin/plink

RUN wget https://raw.githubusercontent.com/h3abionet/h3agwas/master/utils/bin/fastlmmc
RUN mv fastlmmc /usr/local/bin/
RUN chmod a+x /usr/local/bin/fastlmmc

#RUN plink -h
RUN gemma -h


#RUN WGET HTTP://S3.AMAZONAWS.COM/PLINK1-ASSETS/$PLINKSRC && UNZIP $PLINKSRC -D /USR/LOCAL/BIN/ && \

#    RM $PLINKSRC /USR/LOCAL/BIN/TOY.PED /USR/LOCAL/BIN/TOY.MAP /USR/LOCAL/BIN/LICENSE && \
#    CHMOD A+X /USR/LOCAL/BIN/PLINK
#RUN WGET $GEMMAURL && GUNZIP GEMMA-$GEMMAVER-LINUX-STATIC-AMD64.GZ && \
#    MV GEMMA-$GEMMAVER-LINUX-STATIC-AMD64 /USR/LOCAL/BIN/GEMMA && CHMOD +X /USR/LOCAL/BIN/GEMMA
#ENV PYTHONPATH ""
