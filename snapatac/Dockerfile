FROM rocker/tidyverse:3.5
RUN apt-get update


RUN apt-get install -y --allow-unauthenticated gcc make libbz2-dev zlib1g-dev libncurses5-dev  libncursesw5-dev liblzma-dev git

RUN git clone https://github.com/samtools/samtools.git
RUN git clone https://github.com/samtools/htslib.git


RUN apt-get install -y --allow-unauthenticated libcurl4-gnutls-dev libssl-dev
RUN apt-get install -y --allow-unauthenticated build-essential libxml2-dev

RUN apt-get install -y --allow-unauthenticated gfortran autoconf
COPY install.R /
RUN Rscript install.R

RUN Rscript install.R
WORKDIR htslib
RUN git submodule update --init --recursive
RUN autoreconf -i && ./configure && make -j 25 && make install 

WORKDIR /samtools

RUN git checkout develop && ls && autoheader && autoconf -Wno-syntax && ./configure && make -j25 && make install

RUN mkdir /workspace

WORKDIR /workspace


