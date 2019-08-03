FROM centos:7
ENV plinksrc "plink_linux_x86_64_20190617.zip"
ENV bolturl "https://data.broadinstitute.org/alkesgroup/BOLT-LMM/downloads/BOLT-LMM_v2.3.2.tar.gz"
RUN yum install --assumeyes epel-release && yum update --assumeyes --skip-broken &&  yum install --assumeyes wget gcc gfortran python3 python-dev py-pip build-base wget freetype-dev libpng-dev openblas-dev bash python-pip numpy scipy python-matplotlib ipython python-pandas sympy python-nose atlas-devel gcc-c++ unzip
#RUN ln -s /usr/include/locale.h /usr/include/xlocale.h
RUN wget http://s3.amazonaws.com/plink1-assets/$plinksrc && unzip $plinksrc -d /usr/local/bin/ && \
rm $plinksrc /usr/local/bin/toy.ped /usr/local/bin/toy.map /usr/local/bin/LICENSE && \
chmod a+x /usr/local/bin/plink
RUN wget $bolturl && tar zxvf BOLT-LMM_v2.3.2.tar.gz && \
mv BOLT-LMM_v2.3.2/bolt BOLT-LMM_v2.3.2/tables /usr/local/bin/ && chmod a+x /usr/local/bin/bolt
RUN pip install numpy scipy matplotlib pandas scikit-learn==0.19.1 sympy nose fastlmm && \
    chmod a+x /usr/lib64/python2.7/site-packages/fastlmm/association/Fastlmm_autoselect/fastlmmc && \
    ln -s /usr/lib64/python2.7/site-packages/fastlmm/association/Fastlmm_autoselect/fastlmmc /usr/local/bin/
