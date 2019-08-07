FROM centos:7
# ENV bolturl "https://data.broadinstitute.org/alkesgroup/BOLT-LMM/downloads/BOLT-LMM_v2.3.2.tar.gz"
ENV ldscurl "https://github.com/bulik/ldsc.git"
ENV PYTHONNOUSERSITE 1 
# from a running Docker image I called `python -c "import sys; print(':'.join(x for x in sys.path if x))"`
ENV PYTHONPATH /usr/lib64/python27.zip:/usr/lib64/python2.7:/usr/lib64/python2.7/plat-linux2:/usr/lib64/python2.7/lib-tk:/usr/lib64/python2.7/lib-old:/usr/lib64/python2.7/lib-dynload:/usr/lib64/python2.7/site-packages:/usr/lib64/python2.7/site-packages/gtk-2.0:/usr/lib/python2.7/site-packages
RUN yum install --assumeyes epel-release && yum update --assumeyes --skip-broken &&  yum install --assumeyes wget gcc gfortran python3 python-dev py-pip build-base wget freetype-dev libpng-dev openblas-dev bash python-pip numpy scipy python-matplotlib ipython python-pandas sympy python-nose atlas-devel gcc-c++ unzip git zlib-devel bzip2-devel xz-devel libcurl-devel gcc gcc-c++ kernel-devel make
#RUN ln -s /usr/include/locale.h /usr/include/xlocale.h
RUN git clone $ldscurl && cd ldsc && cat environment.yml  | perl -pe 'my $i; while (<>) { chomp; next if (!/^-/ || /^- biocon/ || /^- python/); s/=/==/g; s/- //g; $i .= "$_ "; } print "pip install $i"; exec("pip install $i");' && mv * /usr/local/bin/
