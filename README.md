# Introduction
#### This project aims for solving the ODEs in mircrogird, especially for forward (simulation) and inverse (parameters estimation) calculation of synchronous- and inverter-based DERs. Futhermore, it can be used in microgrid equivalent modeling.

#### If you request collaboration or tech. support, please contact dongxz@whu.edu.cn.

# Env. Info.
#### 1. Our test env: Python Version 3.11 backends PyTorch 2.0.1 + CU117 on NVIDIA A30 × 8
#### 2. RTDS: RSCAD FX Version >= 1.2
# Basic principles plz refer to our papers

>LATEX CITATION:
>
>@unpublished{LikunSchenPESGM2024,  
  author = {Chen, Likun and Dong, Xuzhu and Wang, Yifan and Sun, Wei and Wang, Bo and Harrison, Gareth},  
  title  = {Physics-Informed Neural Network for Microgrid Forward/Inverse Ordinary Differential Equations},  
  note   = {IEEE PES General Meeting},  
  year   = {2024},  
>}
>
>@unpublished{LikunSchenTPS2024,  
  author = {Chen, Likun and Dong, Xuzhu and Wang, Yifan and Sun, Wei and Harrison, Gareth},  
  title  = {Improved PINN-Based Parameters Estimation for Distributed Energy Resources Analysis in Microgrid},  
  note   = {Submitted to IEEE Trans. on Smart Grid},  
  year   = {2024},  
>}
  
# HOW TO USE
The example codes for both sync- and inverter-based DERs are [SYNC_MAIN.py](./PINN-for-Synchronous/SYNC_MAIN.py) and [PID_MAIN.py](./PINN-for-inverter-control-loop/PID_MAIN.py).

Before running, plz remember to install Torch and CUDA correctly.

If any path errors occur, please check **both the absolute and relative paths** of your running environment, if the error message is related to the path for storing the model, please **create a folder named `save_model/` on your own and add the path** accordingly.

The example data files [inverter-based DER data (Name: '0122FltQControl.csv')](./data/inverter-control-loop/0122FltQControl.csv) and [sync-based unit data (Name'927testforTe2.csv')](./data/synchronous-machine/927testforTe2.csv) are both generated by real-time digital simulation (RTDS) system.

Or you can just use the [Auto Running (Name: RunMeEz.py)](./RunMeEz.py) to simultaneously run [SYNC_MAIN.py](./PINN-for-Synchronous/SYNC_MAIN.py) and [PID_MAIN.py](./PINN-for-inverter-control-loop/PID_MAIN.py), povided that your computer is expensive enough, with good RAM and a graphics card.

## About PINN
Physics-Informed Neural Networks (PINNs) have unique advantages in solving Ordinary Differential Equations (ODEs) related to electrical power systems.

The main benefit is the ability to solve both forward and inverse problems with limited data and under conditions where the physical equations are not well-defined.

This capability is precisely why we have applied this method. For a detailed understanding of the principles behind PINNs, refer to the [DEEPXDE](https://deepxde.readthedocs.io/en/latest/index.html).


## About RTDS microgrid model
The established model is saved in `./RTDS-MODEL/SimpleMicrogrid`，the directory contains the following files.
1. `Microgrid1.dfx` : our established model, contains really perfect control and satisfying amount of detailed controls and measurement points XD. (I'm really super satisfied with the microgrid model I've built, even though my supervisor thinks it's quite ordinary. Still, I believe I've done a great job.)
2. `Microgrid1.sib` : runtime file, using this for RTDS simulation while running.
3. `Microgrid1.pdf` : official microgrid introduction document, differs from our model, but still has some reference value.
