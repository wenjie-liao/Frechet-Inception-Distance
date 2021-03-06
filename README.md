# Fréchet Inception Distance
Tensorflow implementation of the "Fréchet Inception Distance" (FID) between two image distributions, along with a numpy interface. The FID can be used to evaluate generative models by calculating the FID between real and fake data distributions (lower is better).

## Major Dependencies
- `tensorflow==1.14` or (`tensorflow==1.15` and `tensorflow-gan==1.0.0.dev0`) or (`tensorflow>=2` and `tensorflow-gan>=2.0.0`)

## Features
- Fast, easy-to-use and memory-efficient
- No prior knowledge about Tensorflow is necessary if your are using CPUs or GPUs
- Makes use of [TF-GAN](https://github.com/tensorflow/gan)
- Downloads InceptionV1 automatically
- Compatible with both Python 2 and Python 3

## Usage
- If you are working with GPUs, use `fid.py`; if you are working with TPUs, use `fid_tpu.py` and pass a Tensorflow Session and a [TPUStrategy](https://www.tensorflow.org/api_docs/python/tf/distribute/experimental/TPUStrategy) as additional arguments.
- Call `get_fid(images1, images2)`, where `images1`, `images2` are numpy arrays with values ranging from 0 to 255 and shape in the form `[N, 3, HEIGHT, WIDTH]` where `N`, `HEIGHT` and `WIDTH` can be arbitrary. `dtype` of the images is recommended to be `np.uint8` to save CPU memory.
- A smaller `BATCH_SIZE` reduces GPU/TPU memory usage, but at the cost of a slight slowdown.
- If you want to compute a general "Fréchet Classifier Distance" with activations (e.g., outputs of the last pooling layer) `act1` and `act2` from another classifier, call `activations2distance(act1, act2)`. `act1` and `act2` can be numpy arrays of a same arbitrary shape `[N, d]`.

## Examples
GPU: [![Example In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1hgJJI5wuILxcHsmrkZMkHJtk6uDlKOwr?usp=sharing)

TPU and TF1: [![Example In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1F0fXOKlzIkOSEAdIRa9oyacW34SUX2_v?usp=sharing)

TPU and TF2: [![Example In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1Cb8erVc-v6zCG-cLfOWCIjFZPl5zQ4jl?usp=sharing) 

## Links

- The Fréchet Inception Distance was proposed in the paper [GANs Trained by a Two Time-Scale Update Rule Converge to a Local Nash Equilibrium ](https://arxiv.org/abs/1706.08500)
- Code for the [Inception Score](https://github.com/tsc2017/Inception-Score)
