# include ../../shared.mk

# CUB_HOME =/home/yzhan846/cub/cub-1.0.2 USERFLAGS=""

SHELL = /bin/bash

ARCH=sm_60
# CUDA toolkit installation path
CUDA_DIR = /usr/local/cuda-9.1

# CUDA driver path
CUDA_DRIVER_DIR = /usr/lib/nvidia-410

# CUDA SDK installation path
SDK_DIR = $(HOME)/GPU-Computing-SDK-4.2.9

# CUDA toolkit libraries
LIB_DIR = $(CUDA_DIR)/lib64

# MPI 
MPI_DIR = $(HOME)/opt/mpich2-1.4.1p1

# compiler
CC = gcc
CC_FLAGS = -O3 

MPICC = mpicc
MPICC_FLAGS = -O5

MPICXX = mpic++

# CUDA compiler
NVCC = $(CUDA_DIR)/bin/nvcc
NVCC_FLAGS = -arch=$(ARCH)  -O3 
# Link
NVCC_INCLUDE = -I. -I$(CUDA_DIR)/include -I$(SDK_DIR)/C/common/inc -I../../common/inc/ -I$(SDK_DIR)/shared/inc -I$(MPI_DIR)/include 
NVCC_LIB = -lcutil_x86_64 -lcuda -lmpich -lmpl -lnccl
NVCC_LIB_PATH = -L. -L$(SDK_DIR)/C/lib -L$(LIB_DIR)/ -L$(SDK_DIR)/shared/lib -L$(MPI_DIR)/lib -L/home/yzhan846/lib/ -L/usr/lib/ -L/usr/lib64 


LINK_FLAG = $(NVCC_INCLUDE) $(NVCC_LIB_PATH) $(NVCC_LIB) -lstdc++ -lm


kmeans: centroids.cu kmeans.cu labels.cu test.cu timer.cu 
	$(NVCC) $(NVCC_FLAGS) $(LINK_FLAG) -lcublas $^ -o $@

clean: 
	rm -f kmeans
