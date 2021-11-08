FROM python:2.7
RUN apt-get update

RUN pip install snaptools

RUN apt-get install -y gcc make libbz2-dev zlib1g-dev libncurses5-dev  libncursesw5-dev liblzma-dev git

RUN git clone https://github.com/samtools/samtools.git
RUN git clone https://github.com/samtools/htslib.git

WORKDIR htslib
RUN git submodule update --init --recursive
RUN autoreconf -i && ./configure && make -j 25 && make install 

WORKDIR /samtools

RUN git checkout develop && ls && autoheader && autoconf -Wno-syntax && ./configure && make -j25 && make install

RUN mkdir /workspace

WORKDIR /workspace
