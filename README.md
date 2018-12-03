# Implementing Push-Pull Efficiently in GraphBLAS

by Carl Yang, Aydin Buluc, John D. Owens

Accepted to ICPP 2018

## Abstract


We factor Beamer's push-pull, also known as direction-optimized breadth-first-search (DOBFS) into 3 separable optimizations, 
and analyze them for generalizability, asymptotic speedup, and contribution to overall speedup. We demonstrate that masking 
is critical for high performance and can be generalized to all graph algorithms where the sparsity pattern of the output is 
known _a priori_. We show that these graph algorithm optimizations, which together constitute DOBFS, can be neatly and 
separably described using linear algebra and can be expressed in the GraphBLAS linear-algebra-based framework. We provide 
experimental evidence that with these optimizations, a DOBFS expressed in a linear-algebra-based graph framework attains 
competitive performance with state-of-the-art graph frameworks on the GPU and on a multi-threaded CPU, achieving 101 GTEPS 
on a Scale 22 RMAT graph.

![](http://wwwimages.adobe.com/content/dam/acom/en/legal/images/badges/Adobe_PDF_file_icon_32x32.png) [pushpull-icpp18-final.pdf](https://github.com/owensgroup/push-pull/raw/master/pushpull-icpp2018-final.pdf)


## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing 
purposes.

### Prerequisites

This software has been tested on the following dependencies:

* CUDA 8.0
* Boost 1.58
* CMake 3.11.1
* g++ 4.9.3
* ModernGPU 1.1

---

### CUDA 8.0

If CUDA 8.0 is not already installed on your system, you will need to download CUDA 8.0 
[here](https://developer.nvidia.com/cuda-80-ga2-download-archive). Follow the onscreen instructions and select the operating system and vendor that suits your needs. Download the 1.4GB file. You do not need to download the optional Patch 2.

After generating a download link, the commands I typed were the following:

```
wget https://developer.nvidia.com/compute/cuda/8.0/Prod2/local_installers/cuda_8.0.61_375.26_linux-run
chmod +x cuda_8.0.61_375.26_linux-run
sudo ./cuda_8.0.61_375.26_linux-run
```

You will need to select:
```
graphics driver: yes
OpenGL: yes
nvidia-xconfig: no
CUDA 8.0: yes
symbolic link: yes
CUDA samples: yes
```

Once installation has finished, check that your installation has completed by typing:

```
nvidia-smi
```

If installation was successful, you should be able to see information about your GPU printed onscreen. 
Check that the right information has been added to your system path by typing:

```
vi ~/.bashrc
```

If not already present, you should append to the bottom:

```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-8.0/lib64
export CUDA_HOME=/usr/local/cuda-8.0
```

Additional instructions on installing CUDA can be found 
[here](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#runfile).

### Boost 1.58

You will need to install or compile Boost 1.58 program options using the same compiler as you do our software. 
To only install Boost program options, type:

```
wget http://sourceforge.net/projects/boost/files/boost/1.58.0/boost_1_58_0.tar.gz
tar -xvzf boost_1_58_0.tar.gz
cd boost_1_58_0
./bootstrap.sh --prefix=path/to/installation/prefix
./b2 --with-program_options
```

### CMake 3.11.1

If not already installed, you will need to install CMake by typing:

```
sudo apt-get install cmake
```

### g++ 4.9.3

You will need g++-4.9. Install by typing:

```
sudo apt-get install gcc-4.9 g++-4.9
```

### ModernGPU 1.1

This excellent software by Sean Baxter will be automatically downloaded as a Git submodule.

## Installing

A step by step series of examples that tell you have to get a development env running.

1. First, we must download the software:

```
git clone --recursive https://github.com/owensgroup/GraphBLAS.git
```

2. Then, we must compile the software.

```
cmake .
make -j16
```

3. Next, we must download the datasets. In order of increasing size, they are listed below and can be downloaded 
automatically.

Small - 10 small row length graphs (400MB)
```
```

Large - 10 large row length graphs (1650MB)
```
```

Super large - 172 graphs (4000MB)
```
```

4. The figures in the paper can be reconstructed by typing:

```
```

## Authors

* **Carl Yang**
* **Aydin Buluc**
* **John D. Owens**

## License

This project is licensed under the Apache License - see the [LICENSE.md](LICENSE) file for details

## Acknowledgments

* A big thanks to Yangzihao and co's [Gunrock paper](https://arxiv.org/pdf/1701.01170.pdf) and [code](https://github.com/gunrock/gunrock) and Scott Beamer's 
[Direction-optimization paper](www.scottbeamer.net/pubs/beamer-sc2012.pdf) which inspired our work.
* Much thanks goes to [Yuechao Pan's](https://sites.google.com/site/panyuechao/home) valuable insights into BFS optimizations
without which this paper would not have been possible.
* Special thanks to Scott McMillan for providing important feedback on early drafts.
