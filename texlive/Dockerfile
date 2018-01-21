FROM centos:centos7

MAINTAINER Eugene de Beste, Scott Hazelhurst

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
    which epel-release
RUN yum install -y \
    python34 python34-libs python34-pip
RUN pip3 install --upgrade pip
RUN pip3 install pandas matplotlib
