# base image
FROM ubuntu:latest

# setup tools and compilers
RUN apt update 
RUN apt install -y tmux && \
    apt install -y htop && \
    apt install -y vim && \
    apt install -y git && \
    apt-get install -y device-tree-compiler

# configuring vim
RUN echo "colorscheme elflord" >> /root/.vimrc && \ 
    echo "set number" >> /root/.vimrc && \
    echo "set tabstop=4 softtabstop=0 expandtab shiftwidth=4 smarttab" >> /root/.vimrc

RUN DEBIAN_FRONTEND="noninteractive" apt-get -y install tzdata

# risc-v toolchain prerequisites
RUN apt-get -y install autoconf automake autotools-dev \
    curl python3 libmpc-dev \
    libmpfr-dev libgmp-dev gawk \
    build-essential bison flex \
    texinfo gperf libtool \
    patchutils bc zlib1g-dev libexpat-dev \
    libusb-1.0-0-dev zlib1g-dev pkg-config

# risc-v toolchain
RUN cd /home && \
    git clone https://github.com/riscv/riscv-gnu-toolchain && \
    cd /home/riscv-gnu-toolchain && \
    ./configure --prefix=/opt/riscv && \
    cd /home/riscv-gnu-toolchain && \
    make && \
    rm -r /home/risc-gnu-toolchain 

RUN export RISCV=/opt/riscv 

# spike
RUN git clone https://github.com/riscv/riscv-isa-sim.git /home/riscv-isa-sim && \
    cd /home/riscv-isa-sim && \
    mkdir build && \
    cd build && \
    ../configure --prefix=$RISCV && \
    make && \
    make install
    
# riscv pk - proxy kernel
RUN export PATH=$PATH:/opt/riscv/bin && \
    cd /home && \
    git clone https://github.com/riscv/riscv-pk.git && \
    cd /home/riscv-pk && \
    mkdir build && \
    cd build && \ 
    ../configure --prefix=$RISCV --host=riscv64-unknown-elf && \
    make && \
    make install

# upadating PATH
RUN echo 'PATH="$PATH:/opt/riscv/bin"' >> /root/.bashrc
