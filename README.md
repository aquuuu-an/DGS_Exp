# Dynamic Graph Storage Survey

This repository provides source code and script in our experiments for reproducing
the experiment in paper, _Dynamic Graph Storage: An Experimental Survey_.

We conduct an extensive survey and evaluation of existing graph storage
systems, focusing on how the storage structures affect different
aspects of performance, e.g., update throughput, lookup efficiency,
algorithm execution time, and memory consumption.

All the experiment systems are open-source, and you can fetch them by the following
links :

**Aspen**: https://github.com/ldhulipala/aspen

**LLAMA**: https://github.com/goatdb/llama

**Teseo**: https://github.com/cwida/teseo

**Terrace**: https://github.com/PASSIONLab/terrace

**Stinger**: https://github.com/the-data-lab/GraphOne

**GraphOne**: https://github.com/the-data-lab/GraphOne

**LiveGraph**: https://github.com/thu-pacman/LiveGraph

**RisGraph**: https://github.com/thu-pacman/RisGraph

**PCSR**: https://github.com/wheatman/Packed-Compressed-Sparse-Row/

## Build

### Environment
- CMake & C++ 17
- G++ 9.4.0 & gcc 7.5.0
- OpenMP
- Clang 10

- Ubuntu 18.04
- CILK
https://izhuhaoran.github.io/2023/01/24/CPP_Note/cilkplus%E5%AD%A6%E4%B9%A0%E8%AE%B0%E5%BD%95/
Ubuntu 20.04移除对CILK库的支持。Ubuntu 18.04直接使用sudo apt install gcc g++，安装的7.5.0版本包含cilk库

- g++ -9
但是Teseo需要g++ -9，所以通过sudo apt install g++-9另外安装一个9.4.0版本
sudo cp -r /usr/lib/gcc/x86_64-linux-gnu/7/include/cilk /usr/lib/gcc/x86_64-linux-gnu/9/include/cilk

### Preconfig

```
git clone https://github.com/xiangyuzhi/GraphStorageExp.git --recursive
cd GraphStorageExp & mkdir build 
cd build
cmake ..
make
```

### Dataset

×无法访问
The dataset can be download form: http://konect.cc/networks/ use:

```
cd data/LDBCgraph
wget http://konect.cc/networks/{exp_data} 
```

√可以访问
The dataset can be download form: https://snap.stanford.edu/data/ use:

```
cd ..
mkdir data
cd data
mkdir LDBCgraph 
cd LDBCgraph

# LiveJournal
wget https://snap.stanford.edu/data/soc-LiveJournal1.txt.gz
gunzip soc-LiveJournal1.txt.gz

# Orkut
wget https://snap.stanford.edu/data/bigdata/communities/com-orkut.ungraph.txt.gz
gunzip com-orkut.ungraph.txt.gz

# Twitter
wget https://snap.stanford.edu/data/twitter_combined.txt.gz
gunzip twitter_combined.txt.gz

# Friendster
wget https://snap.stanford.edu/data/bigdata/communities/com-friendster.ungraph.txt.gz
gunzip com-friendster.ungraph.txt.gz
```

Before run experiment, please transform data from LDBC format to CSR format by use:

```
cd ..
mkdir ADJgraph
cd ../build/exp
./transfer  ../../data/LDBCgraph/{exp_data}.txt  ../../data/ADJgraph/{exp_data}.adj
```

### Run

The experiment for all system can be run following the script:

```
cd exp
./exp.sh
```

### Plot
The figure plot in paper can be reproduced by running the python script in 
exp/plot/exp_data_proc.ipynb

## Authors

- Xiangyu Zhi [zhixy2021@mail.sustech.edu.cn](zhixy2021@mail.sustech.edu.cn)
- Xiao Yan [yanx@sustech.edu.cn](yanx@sustech.edu.cn)
- Keming Li [likm2020@mail.sustech.edu.cn](likm2020@mail.sustech.edu.cn)
- Bo Tang [tangb3@sustech.edu.cn](tangb3@sustech.edu.cn)
- Yanchao Zhu [zhuyanchao2@huawei.com](zhuyanchao2@huawei.com)
- Minqi Zhou [zhouminqi@huawei.com](zhouminqi@huawei.com)



