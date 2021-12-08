# MALRU-Replacement-Policy
Abeer Waheed, CJ Sewell, Subrajit Surendran - CSCE 469/614 Term Project 

## Project Description
This research will focus on the implementation of the MALRU cache replacement policy. 
Miss penalty aware LRU-based cache replacement policy (MALRU) replacement policy is a cache replacement policy that 
hopes to reduce latency by preferenciantially removing DRAM blocks as opposed to NVM blocks.

#### Project Goal
The goal of this research project is to help paint a more informed decision on hybrid cache replacement policies (specifically MALRU), and to see if the performance on single memory applications is good. 
The problem looking to be solved in this research is as follows: How does MALRU work when a majority of data is incoming from only a single source (either NVM or DRAM)?

#### Project Source 
Jim H, Chen D, Liu H, Liao Guo R, Zhang Y. Miss penalty aware cache replacement for hybrid memory systems. IEEE Transactions on Computer-Aided Design of Integrated Circuits and Systems, 2020, 39(12): 4669-4682. DOI: 10.1109/TCAD.2020.2966482
```
https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8957668&tag=1
```
#### Simulator Used
The simulator we are using is Zsim.
ZSim: Fast and Accurate Microarchitectural Simulation of Thousand-Core Systems", Sanchez and Kozyrakis, ISCA-40, June 2013
```
https://people.csail.mit.edu/sanchez/papers/2013.zsim.isca.pdf
```

Project Structure

``` .
    ├── casim             
    │   ├── zsim          # simulator
    │   ├── tools       
    │   └── benchmarks   
    └── ...
    
    ├── zsim             
    │   ├── outputs                     # contains all resulting output files
    │   ├── src 
    │       ├──  malru_repl.h           # contains implementation of MALRU cache replacement policy
    │       ├──  repl_policies.h        # contains LRU
    │       └──  init.cpp               # contains initialization of MALRU and other replacement polcies
    │   ├── configs   
    │       └──  research      # contains MALRU and LRU config files
    │            |── MALRU
    │             └── LRU
    |   └── build
    └── ...
```

## Environment Setup

1) Set up a directory and git clone this repository to access and run the MALRU implementation.
```
$ git clone https://github.tamu.edu/CSCE-614-Dr-Kim-Fall-21/MALRU-Replacement-Policy.git
```

2) Everytime you want to build or run zsim, you need to setup the environment variables first in the casim folder.
```
$ source setup_env
```

3) Go to the zsim folder and compile zsim.
```
$ scons -j16
```

4) To simulate MALRU and LRU on the benchmarks, use the following command:
```
./runscript SPEC <benchmark> <repl_policy>
```
benchmark: bzip2 gcc mcf hmmer sjeng libquantum xalancbmk milc cactusADM leslie3d namd soplex calculix lbm

repl_policy: MALRU or LRU

#### Output file format and file path
Format: zsim.out
MALRU output files:
```
./casim/zsim/outputs/research/MALRU/{benchmark}/zsim.out
```
LRU output files:
```
./casim/zsim/outputs/research/LRU/{benchmark}/zsim.out
```
