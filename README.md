# Super-Resolution datasets for Pytorch

This repository implements datasets and transforms to make Super-Resolution development easy.
It is heavily inspired by [torchvision](https://github.com/pytorch/vision) and [EDSR](https://github.com/zhouhuanxiang/EDSR-PyTorch).


## Usage

```python
from datasets import Div2K
from transforms import Compose, RandomCrop, ColorJitter

# Div2K dataset, cropped to 256px with brightness jitter
dataset = Div2K(root="./data", scale=2, download=False,
                transform=Compose(RandomCrop(256), ColorJitter(brightness=0.2))

# Show the first HR image
hr, lr = dataset[0]
hr.show()
```


## Datasets

Datasets return a list of images. The first image is the original one, and the next images are downscaled or degraded versions.

The following datasets are available, and can be downloaded automatically:
* [DIV2K](https://data.vision.ee.ethz.ch/cvl/DIV2K/)
* [Set5](http://people.rennes.inria.fr/Aline.Roumy/results/SR_BMVC12.html)
* [Set14](https://paperswithcode.com/dataset/set14)
* [B100](https://www2.eecs.berkeley.edu/Research/Projects/CS/vision/bsds/)
* [Urban100](https://paperswithcode.com/dataset/urban100)



## Transforms

Transforms are used for preprocessing and data augmentation. They are applied identically to the original and downscaled image.

This repository defines several transforms that follow torchvision conventions:
* ToTensor/ToPILImage
* Compose
* RandomCrop
* ColorJitter
* GaussianBlur
* RandomHorizontalFlip/RandomVerticalFlip
