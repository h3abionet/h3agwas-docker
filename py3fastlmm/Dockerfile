FROM centos:7
ENV plinksrc "plink_linux_x86_64_20190617.zip"
# ENV bolturl "https://data.broadinstitute.org/alkesgroup/BOLT-LMM/downloads/BOLT-LMM_v2.3.2.tar.gz"
ENV bolturl "https://data.broadinstitute.org/alkesgroup/BOLT-LMM/downloads/old/BOLT-LMM_v2.3.2.tar.gz"
ENV PYTHONNOUSERSITE 1 
RUN yum install --assumeyes epel-release && yum update --assumeyes --skip-broken &&  yum install --assumeyes wget gcc gfortran python3-devel build-base wget freetype-dev libpng-dev openblas-dev bash python3-pip  sympy  atlas-devel gcc-c++ unzip cmake3 libzstd-devel zlib zlib-devel scl-utils devtoolset-8 centos-release-scl-rh git
RUN ln -s /usr/bin/cmake3 /usr/local/bin/cmake && ln -s /usr/bin/ctest3 /usr/local/bin/ctest
RUN python3 -m pip install pip setuptools --upgrade
RUN python3 -m pip install numpy scipy psutil wheel

RUN git clone https://github.com/horta/almosthere && cd almosthere && mkdir build && cd build && cmake .. -DCMAKE_BUILD_TYPE=Release -DBUILD_SHARED_LIBS=ON &&  make && make test && make install
# We need a version of gcc  > the default so we enable devtoolset which gives us gcc-8
# that's what scl enable does 
RUN scl enable devtoolset-8 "curl -fsSL https://git.io/JerYI | GITHUB_USER=limix GITHUB_PROJECT=bgen bash"
RUN scl enable devtoolset-8 "python3 -m pip install bgen-reader"
RUN python3 -m pip install fastlmm
RUN python3 -m pip install matplotlib pandas scikit-learn sympy nose  --upgrade
RUN wget http://s3.amazonaws.com/plink1-assets/$plinksrc && unzip $plinksrc -d /usr/local/bin/ && \
rm $plinksrc /usr/local/bin/toy.ped /usr/local/bin/toy.map /usr/local/bin/LICENSE && \
chmod a+x /usr/local/bin/plink
RUN wget $bolturl && tar zxvf BOLT-LMM_v2.3.2.tar.gz && \
mv BOLT-LMM_v2.3.2/bolt BOLT-LMM_v2.3.2/tables /usr/local/bin/ && chmod a+x /usr/local/bin/bolt
RUN chmod a+x /usr/local/lib64/python3.6/site-packages/fastlmm/association/Fastlmm_autoselect/fastlmmc && ln -s /usr/local/lib64/python3.6/site-packages/fastlmm/association/Fastlmm_autoselect/fastlmmc /usr/local/bin/fastlmmc
