FROM quay.io/cybozu/ubuntu:20.04
ENV PYTHONNOUSERSITE 1  
RUN apt-get -y update && apt-get -y install build-essential python3-dev python3 python3-pip gfortran wget libpng-dev libopenblas-dev  ca-certificates 
#RUN ln -s /usr/include/locale.h /usr/include/xlocale.h
RUN pip3 install numpy scipy pandas==2.0.0 matplotlib openpyxl biopython Distance
RUN mkdir plink && cd plink && wget -c https://s3.amazonaws.com/plink1-assets/plink_linux_x86_64_20260927.zip && unzip plink_linux_x86_64_20260927.zip && cp plink /usr/bin/plink && cd ../ && rm -rf plink && chmod +x /usr/bin/plink
RUN mkdir plink2 && cd plink2 && wget -c https://s3.amazonaws.com/plink2-assets/beta1/plink2_linux_avx2_20261024.zip && unzip plink2_linux_avx2_20261024.zip && cp plink2 mtag ldsc vcf_subset /usr/bin/ && cd ../ && rm -rf plink2 && chmod +x /usr/bin/plink2 /usr/bin/mtag /usr/bin/ldsc /usr/bin/vcf_subset
RUN mkdir -p magma && cd magma && wget -O magma.zip -c https://vu.data.surf.nl/public.php/dav/files/zkKbNeNOZAhFXZB/?accept=zip -o magma.zip && unzip magma.zip && make && mv magma /usr/bin/ && chmod +x /usr/bin/magma
