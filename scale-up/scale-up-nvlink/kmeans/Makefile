# include ../../shared.mk

# CUB_HOME =/home/yzhan846/cub/cub-1.0.2 USERFLAGS=""




kmeans: centroids.cu kmeans.cu labels.cu test.cu timer.cu 
	$(NVCC) $(NVCC_FLAGS) $(LINK_FLAG) -lcublas $^ -o $@

clean: 
	rm -f kmeans
