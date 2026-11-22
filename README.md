# Generative Models Comparison on Fashion-MNIST

## Requirements

- Python 3.12
- NVIDIA GPU with CUDA (recommended). CPU also works but is much slower.

## Setup

1. Clone the repository.
   ```
    git clone https://github.com/saaaileen/assignment_deeplearning.git
    cd assignment_deeplearning
   ```
2. Create a virtual environment.
   ```
    py -3.12 -m venv environments/deep_learning
   ```
3. Activate it.
   ```
   environments/deep_learning/Scripts/Activate.bat
   ```
4. Install the packages.
   ```
    pip install --upgrade pip
    pip install -r requirements.txt
   ```

    If you do not have an NVIDIA GPU, remove the `--extra-index-url` line and the `+cu124` parts in `requirements.txt` first.
5. Register the Jupyter kernel.
   ```
   1. Go to visual studio code
   2. ctrl + shift + p -> select python interpreter
   3. Click enter interpreter path -> Find
   4. Go to environments folder and go to scripts and click python
   ```

## How to Run

Open the notebooks with the `deep_learning` kernel and run them in this order.


| Step | Notebook                  | What it does                             | Time (RTX 4060) |
| ---- | ------------------------- | ---------------------------------------- | --------------- |
| 1    | `01_vanilla_ae.ipynb`     | Train Vanilla AE                         | about 1 min     |
| 2    | `02_sparse_ae.ipynb`      | Train Sparse AE                          | about 1 min     |
| 3    | `03_vae.ipynb`            | Train VAE                                | about 1 min     |
| 4    | `04_vanilla_gan.ipynb`    | Train Vanilla GAN                        | about 2 min     |
| 5    | `05_dcgan.ipynb`          | Train DCGAN                              | about 3 min     |
| 6    | `06_ddpm.ipynb`           | Train DDPM                               | about 30 min    |
| 7    | `07_mlp_classifier.ipynb` | MLP classifier experiment                | about 2 min     |
| 8    | `08_comparison.ipynb`     | Make the metrics table and the 5 figures | under 1 min     |


Notebook 07 needs the result of notebook 01. Notebook 08 needs the results of notebooks 01 to 07.

The dataset downloads automatically to `data/` the first time you run a notebook.

## Experiment Settings

All models use the same settings:

- Dataset: Fashion-MNIST, 70,000 images (train and test combined)
- Split: 80% train, 10% validation, 10% test
- Random seed: 42
- Batch size: 128
- Shuffle: on for train, off for validation and test
- Epochs: 30
- All metrics are measured on the test set

## Output


| Folder         | Content                                                                                                                              |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| `results/`     | Metrics for each model (`.json`), the metrics table (`metrics_table.csv`), and the MLP experiment table (`mlp_limitation_table.csv`) |
| `figures/`     | The 5 figures used in the report                                                                                                     |
| `checkpoints/` | Trained model weights (not uploaded to GitHub)                                                                                       |


## Metrics

- Reconstruction: MSE, PSNR, SSIM
- Generation: FID (7,000 generated images vs. 7,000 test images)
- Speed: training time per epoch, and inference time for one batch of 64 images