#Download base image ubuntu 19.10
FROM ubuntu:19.10

# Update Ubuntu Software repository
RUN apt-get update

RUN apt-get install -y build-essential ssh openssh-server cmake gfortran python3-pip python3-dev python3-numpy
WORKDIR /home
RUN mkdir openmpi
WORKDIR openmpi
RUN wget https://download.open-mpi.org/release/open-mpi/v4.0/openmpi-4.0.2.tar.gz
RUN tar -xvf openmpi-4.0.2.tar.gz
WORKDIR openmpi-4.0.2
RUN ./configure CC=/usr/bin/gcc CXX=/usr/bin/g++ FC=/usr/bin/gfortran F77=/usr/bin/gfortran
RUN make -j8
RUN make install
RUN ldconfig
WORKDIR /home
RUN mkdir hdf5
WORKDIR hdf5
RUN wget https://github.com/live-clones/hdf5/archive/hdf5-1_10_5.tar.gz
RUN tar -xvf hdf5-1_10_5.tar.gz
WORKDIR hdf5-hdf5-1_10_5
RUN ./configure --enable-fortran --enable-build-mode=production --enable-parallel CC=mpicc CXX=mpic++ FC=mpif90 F77=mpif90
RUN make -j8
RUN make install
RUN ldconfig
WORKDIR /
