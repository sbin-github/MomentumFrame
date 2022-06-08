# Momentum-frame Based 2D Physix


## 0. Prerequisites

From this directory, run below in your terminal:

<code>$ mkdir solvers/data/model & mkdir solvers/data/gif_deeper & mkdir solvers/data/npy</code>

And please make sure that you have python modules in "requirements.txt".

We do not recommend using "-r install", as it includes pytorch and taichi.

Please visit "https://docs.taichi.graphics/docs/" if you want to know about taichi for python.


## 1. Generate Ground-truth from Taichi Simulation

You can do it by running "solvers/1_generate_simulation_data.py".

**Please run it in the local directory!**

It will automatically generate momentum-frame dataset in .npy format.

You need at least 350 datasets to run the code without modifications.


## 2. Generate Pytorch Tensor Trainset/Testset

Please use "solvers/learning/2_generate_pt_dataset.ipynb".

If your .npy data are located correctly, it will save .pt datasets.


## 3. Training

Enjoy your training with "solvers/learning/3_training.ipynb".

In our experience, it will give satisfying results after about 15 epochs in the current setup.

We recommend you use RTX-3090 or other GPUs with larger memory sizes.

You may modify the "batch_size" hyperparameter if your GPU runs out of memory.

Please note that you may need to change learning rates also in that case.


## 4. Visualization

You can use "solvers/learning/4_visualization.ipynb".

It generates sequence images or gif files.

Please note that they use your testset, not the trainingset.