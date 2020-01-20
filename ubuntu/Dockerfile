FROM ubuntu:19.10
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && apt-get install -y apt-utils
RUN apt-get upgrade -y
RUN apt-get install -y build-essential libssl-dev wget python3 python3-dev python3-pip python3-tk python3-numpy python3-matplotlib
WORKDIR /home
RUN mkdir cmake
WORKDIR cmake
RUN wget https://github.com/Kitware/CMake/releases/download/v3.16.2/cmake-3.16.2.tar.gz
RUN tar -xf cmake-3.16.2.tar.gz
WORKDIR cmake-3.16.2
RUN ./bootstrap
RUN make -j4
RUN make install
RUN ldconfig
WORKDIR /home
RUN rm -rf cmake
WORKDIR /
ENV DEBIAN_FRONTEND teletype