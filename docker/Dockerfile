# FROM ubuntu:22.04
#FROM nvidia/cuda:11.3.1-devel-ubuntu20.04
FROM nvidia/cuda:12.1.0-devel-ubuntu22.04

ENV DEBIAN_FRONTEND noninteractive

# Some system dependencies
RUN apt-get update && \
    apt-get install -y mlocate less git cmake-curses-gui cmake-gui jq wget unzip debconf-utils

# RUN git clone https://github.com/uzh-rpg/dagr.git
RUN git clone https://github.com/AndreasAZiegler/dagr.git

RUN mkdir -p /miniconda3 && \
    wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O /miniconda3/miniconda.sh && \
    bash /miniconda3/miniconda.sh -b -u -p /miniconda3 && \
    chmod -R 755 /miniconda3 && \
    rm -rf /miniconda3/miniconda.sh

ENV PATH="/miniconda3/bin:$PATH" 

RUN conda init bash && \
    bash ~/.bashrc && \
    . ~/.bashrc && \
    conda create -y -n dagr python=3.8 && \
    conda activate dagr && \
    #conda install -y setuptools==69.5.1 anaconda::mkl pytorch==1.11.0 torchvision==0.12.0 torchaudio==0.11.0 cudatoolkit=11.3 -c pytorch
    conda install -y setuptools==69.5.1 anaconda::mkl pytorch torchvision torchaudio pytorch-cuda=12.1 pytorch-sparse pytorch-scatter pytorch-cluster pytorch-spline-conv -c pytorch -c nvidia -c pyg  && \
    conda install -y h5py conda-forge::blosc-hdf5-plugin

RUN apt-get update && \
    apt-get install -y g++

RUN conda init bash && \
    . ~/.bashrc && \
    conda activate dagr && \
    cd /dagr && \
    bash install_env.sh

#RUN conda init bash && \
#    . ~/.bashrc && \
#    conda activate dagr && \
#    cd /dagr && \
#    bash download_and_install_dependencies.sh && \

RUN rm -rf /dagr

RUN chmod -R 755 /miniconda3

ENV CUDA_HOME=/usr/local/cuda

ENV NVIDIA_VISIBLE_DEVICES all
ENV NVIDIA_DRIVER_CAPABILITIES compute,utility

#RUN conda init bash && \
#    . ~/.bashrc && \
#    conda activate dagr && \
#    cd /dagr && \
#    pip install -e .
