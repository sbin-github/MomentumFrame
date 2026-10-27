# Momentum-Frame-Based 2D Physics

## 0. Prerequisites

Create the required directories from the project root:

```bash
mkdir -p solvers/data/{model,gif_deeper,npy}
```

Install the dependencies listed in `requirements.txt`. We recommend installing them individually rather than using `pip install -r requirements.txt`, as the file includes PyTorch and Taichi.

For Taichi documentation, visit [Taichi Docs](https://docs.taichi-lang.org/).

## 1. Generate Simulation Data

Run `solvers/1_generate_simulation_data.py` from the project root to generate ground-truth momentum-frame datasets in `.npy` format.

**At least 350 datasets are required** with the default configuration.

## 2. Prepare Training and Test Datasets

Run `solvers/learning/2_generate_pt_dataset.ipynb` to convert the generated `.npy` files into PyTorch `.pt` datasets.

## 3. Training

Run `solvers/learning/3_training.ipynb` to train the model.

Training typically achieves satisfactory results within approximately **15 epochs**.

An RTX 3090 or a GPU with comparable or greater memory is recommended. If GPU memory is insufficient, reduce `batch_size` and adjust the learning rate accordingly.

## 4. Visualization

Run `solvers/learning/4_visualization.ipynb` to generate image sequences or GIF animations.

**Note:** Visualizations use the test dataset, not the training dataset.

## 5. Quick Start: End-to-End

From the project root, run:

```bash
# 1. Create directories
mkdir -p solvers/data/{model,gif_deeper,npy}

# 2. Generate simulation data
python solvers/1_generate_simulation_data.py

# 3. Prepare datasets, train, and visualize
jupyter nbconvert --to notebook --execute --inplace solvers/learning/2_generate_pt_dataset.ipynb
jupyter nbconvert --to notebook --execute --inplace solvers/learning/3_training.ipynb
jupyter nbconvert --to notebook --execute --inplace solvers/learning/4_visualization.ipynb
```

Ensure all dependencies are installed before execution. The commands assume the notebooks support non-interactive execution and use paths relative to the project root.
