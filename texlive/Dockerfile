FROM centos:centos7

LABEL maintainer="Scott.Hazelhurst@wits.ac.za"

# Install the packages needed to work with latex

RUN yum install -y texlive-base \ 
    texlive-tex \ 
    texlive-pdftex \ 
    texlive-geometry \ 
    texlive-datetime \ 
    texlive-pdftex-bin \ 
    texlive-texconfig \ 
    texlive-etex \ 
    texlive-cm \ 
    texlive-latex-fonts \ 
    texlive-latex-bin \ 
    texlive-pdftex-def \ 
    texlive-fancyhdr \
    texlive-ifluatex \
    which epel-release \
RUN yum install -y \
    python36 python36-libs python36-pip
RUN python3 -m pip  install --upgrade awscli
ENV PYTHONNOUSERSITE 1 
ENV PYTHONPATH  ""

