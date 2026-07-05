# Thesis Title: How Much Data is Enough? A Learning Curve Analysis on Fashion-MNIST and MNIST

## Abstract

The exact quantity of training data required for reliable image classification is rarely known in advance, leading organisations to suffer overcollection costs. In this thesis, the effects training set size has on the test accuracy of a fixed shallow convolutional neural network (CNN) on Fashion-MNIST and MNIST, two structurally similar benchmark datasets differing primarily in their visual class complexity is investigated. To achieve this, learning curves were measured at seven training set sizes spanning between 600 to 60,000 images, fitted to a power-law function, and their plateaus were evaluated. For both datasets the power law function with R² ≥ 0.998 was observed, although with different scaling. MNIST plateaued at about 9,200 images, while Fashion-MNIST did not within an extrapolated range of 500,000 images. This large data dependence is attributed to the visual complexity of the clothing categories. A sparse architecture was trained on external-contour-only outlines, it reached 97.7% accuracy on MNIST but its estimated accuracy ceiling was eight percentage points below the dense model on Fashion-MNIST, an indication that interior texture is an essential signal for clothing classification. The kernel activation pattern experiments demonstrated that border ring kernels match the accuracy of fully dense kernels, while the removal of spatial context is the most negative impact when the input is sparsest. In conclusion, the learning curve and configuration experiments provide a practical basis for data collection decisions in comparable small scale image classification contexts. 

## Expected Outputs:
- A Python implementation in Google Colab containing the code for preprocessing, stratified subsampling, dense and sparse model training, kernel pattern masking, power-law fitting, and visualisations.
- Learning curve tables and plots for both datasets and both architectures.
- Power-law fit results and plateau estimates for both datasets and architectures.
- A per-class F1 analysis for Fashion-MNIST identifying the clothing categories that are most and least dependent on data.
- Kernel pattern experiment results across 11 configurations, three kernel sizes, two architectures, and two datasets.
- Hyperparameter tuning results comparing 11 OFAT configurations for all seven training set sizes, both architectures, and both datasets.

## Running the code
The notebooks were run on Google Colab with an NVIDIA A100 GPU (40 GB). The dense
experiments run on any GPU runtime. The sparse experiments use a custom
`SparseConv2D` layer built on `tf.map_fn` and are slow regardless of the GPU used
(see thesis Section 3.13).

1. Open a notebook in Colab.
2. Mount Google Drive when prompted.
   - (The hyperparameter tuning notebook saves its results to your Drive's
     `thesis_checkpoints/` folder after every seed, so an interrupted session can
     be rerun and will continue from the last saved point.)
3. Run the setup cells (1–5) before any experiment cell. Experiment cells 6–10 are
   independent of each other.
4. Cells 1 through 9 are in a file loaded from Google Colab named: Dense_Sparse_Experiments.ipynb
5. Cell 10 in a seperate file loaded from Google Colab named: Dense_Sparse_HOP_Experiments.ipynb
   

Datasets (Fashion-MNIST, MNIST) are downloaded automatically through `keras.datasets`.

The `results/` folder contains the raw per-seed test accuracies (JSON) for every run.

## Environment

Python        : 3.12.13
TensorFlow    : 2.20.0
Keras         : 3.13.2
NumPy         : 2.0.2
scikit-learn  : 1.6.1
SciPy         : 1.16.3
OpenCV        : 4.13.0
Matplotlib    : 3.10.0

## Citation
Marie Agathe Dalilah Biamby (2026). How Much Data is Enough? A Learning Curve
Analysis on Fashion-MNIST and MNIST. B.Sc. thesis, IU International University
of Applied Sciences.




