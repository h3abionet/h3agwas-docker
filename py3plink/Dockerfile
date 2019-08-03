
FROM alpine:3.7
ENV plinksrc "plink_linux_x86_64_20190617.zip"
ENV gemmaver "0.98.1"
ENV gemmaurl "https://github.com/genetics-statistics/GEMMA/releases/download/0.98.1/gemma-0.98.1-linux-static.gz"
RUN apk --no-cache --update-cache add gcc gfortran python3 python3-dev py3-pip build-base wget freetype-dev libpng-dev openblas-dev bash
RUN ln -s /usr/include/locale.h /usr/include/xlocale.h
RUN pip3 install numpy scipy pandas matplotlib openpyxl biopython Distance
RUN wget http://s3.amazonaws.com/plink1-assets/$plinksrc && unzip $plinksrc -d /usr/local/bin/ && \
    rm $plinksrc /usr/local/bin/toy.ped /usr/local/bin/toy.map /usr/local/bin/LICENSE && \
    chmod a+x /usr/local/bin/plink
RUN wget $gemmaurl && gunzip gemma-${gemmaver}-linux-static.gz && \
    mv gemma-${gemmaver}-linux-static /usr/local/bin/gemma && chmod +x /usr/local/bin/gemma
