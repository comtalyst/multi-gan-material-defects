# Under Construction

# Generating Multiple Objects at Spatially Distinct Locations
Pytorch implementation for reproducing the results from the paper [Generating Multiple Objects at Spatially Distinct Locations](https://openreview.net/forum?id=H1edIiA9KQ) by Tobias Hinz, Stefan Heinrich, and Stefan Wermter accepted for publication at the [International Conference on Learning Representations](https://iclr.cc/) 2019.

![Model-Architecture](examples/model.png)

# Dependencies
- python 2.7
- pytorch 0.4.1

Please add the project folder to PYTHONPATH and install the required dependencies:

```
pip install -r requirements.txt
```

# Data
- Multi-MNIST:
    - contains the three data sets used in the paper: normal (three digits per image), split_digits (0-4 in top half of image, 5-9 in bottom half), and bottom_half_empty (no digits in bottom half of the image)
    - [download](https://www.inf.uni-hamburg.de/en/inst/ab/wtm/research/software/multiple-objects-gan/data-multi-mnist.zip) our data, save it to `data/` and extract
- CLEVR:
    - Main: [download](https://www.inf.uni-hamburg.de/en/inst/ab/wtm/research/software/multiple-objects-gan/data-clevr-main.zip) our data, save it to `data/` and extract
    - CoGenT: [download](https://www.inf.uni-hamburg.de/en/inst/ab/wtm/research/software/multiple-objects-gan/data-clevr-cogent.zip) our data, save it to `data/` and extract
- MS-COCO:
    - obtain the train and validation images from the 2014 split [here](http://cocodataset.org/#download), extract and save them in `data/coco/train/` and `data/coco/test/`
    - [download](https://www.inf.uni-hamburg.de/en/inst/ab/wtm/research/software/multiple-objects-gan/data-ms-coco.zip) our preprocessed data (bounding boxes and bounding box labels) and save it in `data/coco/train/` and `data/coco/test/`
    - for the StackGAN architecture: obtain the preprocessed char-CNN-RNN text embeddings from [here](https://github.com/hanzhanggit/StackGAN-Pytorch)
    - for the AttnGAN architecture: obtain the preprocessed metadata and the pre-trained DAMSM model from [here](https://github.com/taoxugit/AttnGAN)

# Training
- to start training run `sh train.sh data gpu-ids` where you choose the desired data set and architecture (mnist/clevr/coco-stackgan-1/coco-stackgan-2/coco-attngan) and which/how many gpus to train on
- e.g. to train on the Multi-MNIST data set on one GPU: `sh train.sh mnist 0`
- e.g. to train the AttnGAN architecture on the MS-COCO data set on three GPUs: `sh train.sh coco-attngan 0,1,2`
- results are stored in `output/`

# Evaluating
- update the eval cfg file in `code/dataset/cfg/dataset_eval.yml` and adapt the path of `NET_G` to point to the model you want to use
- run `sh sample.sh mnist/clevr/coco-stackgan-1/coco-stackgan-2/coco-attngan` to generate images using the specified model

# Pretrained Models
- pretrained model for Multi-MNIST: [download](https://www.inf.uni-hamburg.de/en/inst/ab/wtm/research/software/multiple-objects-gan/model-multi-mnist.zip) and save to `models`
- pretrained model for CLEVR: [download](https://www.inf.uni-hamburg.de/en/inst/ab/wtm/research/software/multiple-objects-gan/model-clevr.zip) and save to `models`
- pretrained model for MS-COCO:
    - StackGAN architecture: [download](https://www.inf.uni-hamburg.de/en/inst/ab/wtm/research/software/multiple-objects-gan/model-ms-coco-stackgan.zip) and save to `models`
    - AttnGAN architecture: [download](https://www.inf.uni-hamburg.de/en/inst/ab/wtm/research/software/multiple-objects-gan/model-ms-coco-attngan.zip) and save to `models`

# Examples Generated by the Pretrained Models
### Multi-MNIST
![Multi-Mnist Examples](examples/multi-mnist_example.png)

### CLEVR
![CLEVR Examples](examples/clevr_example.png)

### MS-COCO
##### StackGAN Architecture
![COCO-StackGAN Examples](examples/coco_stackgan_example.png)

##### AttnGAN Architecture
![COCO-AttnGAN Examples](examples/coco_attngan_example.png)

# Acknowledgement
- Code for the experiments on Multi-MNIST and CLEVR data sets is adapted from [StackGAN-Pytorch](https://github.com/hanzhanggit/StackGAN-Pytorch).
- Code for the experiments on MS-COCO with the StackGAN architecture is adapted from [StackGAN-Pytorch](https://github.com/hanzhanggit/StackGAN-Pytorch), while the code with the AttnGAN architecture is adapted from [AttnGAN](https://github.com/taoxugit/AttnGAN).

# Citing
If you find our model useful in your research please consider citing:

```
@inproceedings{hinz2019generating,
title     = {Generating Multiple Objects at Spatially Distinct Locations},
author    = {Tobias Hinz and Stefan Heinrich and Stefan Wermter},
booktitle = {International Conference on Learning Representations},
year      = {2019},
url       = {https://openreview.net/forum?id=H1edIiA9KQ},
}
```
