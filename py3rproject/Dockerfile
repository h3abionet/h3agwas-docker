FROM rocker/r-ver:4.6.1

LABEL maintainer="H3ABioNet"
LABEL description="H3AGWAS R/Python/Ruby environment"

ENV DEBIAN_FRONTEND=noninteractive

# ============================================================
# System dependencies
# ============================================================

RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    wget \
    curl \
    unzip \
    ca-certificates \
    cmake \
    pandoc \
    ruby \
    ruby-dev \
    python3 \
    python3-pip \
    python3-dev \
    \
    # R package compilation / networking
    libuv1-dev \
    libcurl4-openssl-dev \
    libssl-dev \
    libxml2-dev \
    \
    # Graphics
    libfontconfig1-dev \
    libfreetype6-dev \
    libpng-dev \
    libjpeg-dev \
    libtiff5-dev \
    libharfbuzz-dev \
    libfribidi-dev \
    libgl1-mesa-dev \
    \
    # Compression
    zlib1g-dev \
    libbz2-dev \
    liblzma-dev \
    \
    # Git / R package dependencies
    libgit2-dev \
    && rm -rf /var/lib/apt/lists/*


# ============================================================
# Python
# ============================================================

RUN pip3 install --no-cache-dir --break-system-packages \
    awscli \
    numpy \
    scipy \
    pandas \
    matplotlib \
    openpyxl \
    biopython \
    Distance


# ============================================================
# R packages
# ============================================================

ENV MAKEFLAGS="-j$(nproc)"

RUN R -e "install.packages(c( \
    'optparse', \
    'data.table', \
    'ggplot2', \
    'ff', \
    'readxl', \
    'svglite', \
    'gridExtra', \
    'openxlsx', \
    'kableExtra', \
    'plyr', \
    'knitr', \
    'qqman', \
    'car' \
), repos='https://cloud.r-project.org', dependencies=TRUE)"


# ============================================================
# R packages needed by rmarkdown / reporting
# ============================================================

RUN R -e "install.packages(c( \
    'htmlTable', \
    'rmarkdown', \
    'Hmisc' \
), repos='https://cloud.r-project.org', dependencies=TRUE)"


# ============================================================
# fastman
# ============================================================

RUN R -e "install.packages( \
    'remotes', \
    repos='https://cloud.r-project.org' \
)"

RUN R -e "remotes::install_github( \
    'adhikari-statgen-lab/fastman' \
)"


# ============================================================
# Verify R packages
# ============================================================

RUN R -e " \
    library(optparse); \
    library(data.table); \
    library(fastman); \
    library(ggplot2); \
    library(ff); \
    library(readxl); \
    library(svglite); \
    library(gridExtra); \
    library(openxlsx); \
    library(kableExtra); \
    library(plyr); \
    library(knitr); \
    library(qqman); \
    library(car); \
    library(htmlTable); \
    library(rmarkdown); \
    library(Hmisc); \
    cat('All R packages loaded successfully\\n') \
"

RUN R -e "install.packages(c( \
    'DT', \
    'plotly', \
    'gt', \
    'htmltools' \
), repos='https://cloud.r-project.org')"

# ============================================================
# PLINK 1.9
# ============================================================
#https://s3.amazonaws.com/plink1-assets/plink_linux_x86_64_20260927.zip
RUN mkdir -p /tmp/plink && \
    cd /tmp/plink && \
    wget -q \
    https://s3.amazonaws.com/plink1-assets/plink_linux_x86_64_20260927.zip && \
    unzip -q plink_linux_x86_64_20260927.zip && \
    install -m 755 plink /usr/local/bin/plink && \
    cd / && \
    rm -rf /tmp/plink

RUN mkdir -p /tmp/plink2 && \
    cd /tmp/plink2 && \
    wget -q \
    https://s3.amazonaws.com/plink2-assets/plink2_linux_x86_64_20260929.zip && \
    unzip -q plink2_linux_x86_64_20260929.zip && \
    install -m 755 plink2 /usr/local/bin/plink2 && \
    cd / && \
    rm -rf /tmp/plink2



# ============================================================
# Verify external tools
# ============================================================

RUN R --version && \
    python3 --version && \
    pip3 --version && \
    ruby --version && \
    plink --version && \
    plink2 --version 

RUN apt-get update && apt-get install -y \
    wget \
    curl \
    ca-certificates \
    git \
    pandoc \
    && rm -rf /var/lib/apt/lists/*

# Install Quarto
RUN wget -c https://github.com/quarto-dev/quarto-cli/releases/download/v1.10.18/quarto-1.10.18-linux-amd64.deb  \
    -O /tmp/quarto.deb \
    && apt-get update \
    && apt-get install -y /tmp/quarto.deb \
    && rm /tmp/quarto.deb \
    && rm -rf /var/lib/apt/lists/*

RUN quarto --version
RUN quarto check install


RUN R -e "install.packages(c('dplyr','tidyr'))"
ARG LOCUSPLOT_VERSION=1

RUN R -e "remotes::install_github('jeantristanb/locusplotr@test')"  
# ============================================================
# Default command
# ============================================================

CMD ["R"]
