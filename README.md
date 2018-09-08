# OCNet: Object Context Network for Scene Parsing (pytorch)

![Overall Framework of OCNet](OCNet.png?raw=true)

Please check the paper [OCNet](https://arxiv.org/pdf/1809.00916.pdf) here.

**We will release all of implementation once the star count exceeds** <font color=red>100</font>.

You are welcome to share our work with your friends. [zhihu share](https://zhuanlan.zhihu.com/p/43902175)

Please consider citing our work if you find it helps you,
```
@article{OCNet,
  title={OCNet: Object Context Network for Scene Parsing},
  author={Yuhui Yuan, Jingdong Wang},
  journal={arXiv preprint arXiv:1809.00916},
  year={2018}
}
```

## Introduction

Context is essential for various computer vision tasks.
The state-of-the-art scene parsing methods have exploited the effectiveness of the context defined over image-level.
Such context carries the mixture of objects belonging to different categories.

According to that the label of each pixel is defined as the category of the object it belongs to, we propose the Object Context that considers the objects belonging to the same category. 
The representation of any pixel P's object context is the aggregation of all the pixels' features that belong to the same category with P.
Since it is impractical to estimate all the objects belonging to the same category in advance,
we employ the self-attention method to approximate the objects by learning a pixel-wise similarity map.

We further propose the Pyramid Object Context and Atrous Spatial Pyramid Object Context to capture context of multiple scales.
Based on the object context, we introduce the OCNet and show that OCNet achieves state-of-the-art performance on both Cityscapes benchmark and ADE20K benchmark.


## Visualization of the learned Object Context
![Object Context learned with OCNet](OCNet_intro.jpg?raw=true)

## Experiment Results
All of our implementation is based on pytorch, OCNet can achieve competitive performance on various benchmarks such as Cityscapes and ADE20K without any bells and whistles.

The current performance on the Cityscapes test set of OCNet trained with only the fine-labeled set,


Method | Conference | Backbone | mIoU(\%) 
---- | --- | --- | --- 
RefineNet |  CVPR2017  | ResNet-101  |  73.6 
SAC  |  ICCV2017  | ResNet-101  |  78.1 
PSPNet |  CVPR2017  | ResNet-101  |  78.4
DUC-HDC | WACV2018 | ResNet-101 | 77.6 
AAF |   ECCV2018  | ResNet-101  |  77.1 
BiSeNet |   ECCV2018  | ResNet-101  |  78.9 
PSANet |  ECCV2018  | ResNet-101  |  80.1 
DFN  |  CVPR2018  | ResNet-101  |  79.3 
DSSPN | CVPR2018  | ResNet-101  | 77.8 
DenseASPP  |  CVPR2018  | DenseNet-161  |  80.6
**OCNet** | - |  ResNet-101 | **81.2**


The current performance on the ADE20K validation set of the OCNet


Method | Conference | Backbone | mIoU(\%) 
---- | --- | --- | --- 
RefineNet | CVPR2017  | ResNet-152  |  40.70  
PSPNet | CVPR2017  | ResNet-101  |  43.29 
SAC |  ICCV2017  |  ResNet-101  |  44.30  
PSANet  |  ECCV2018  |  ResNet-101  |  43.77  
EncNet |  CVPR2018  | ResNet-101  |  44.65
**OCNet** | - |  ResNet-101 | **45.08**


## Enviroment
The code is developed using python 3.5+ on Ubuntu 16.04. NVIDIA GPUs ared needed. The code is tested using 4 NVIDIA P100 GPUS cards.
All the experiments on Cityscapes should run on pytorch0.3 because we find that pytorch0.4 can lead 1 point performance drop(we have not found the bug).

## Quick start


### Requirements
~~~~
torch=0.3
torchvision
tensorboardX
pillow
tqdm
h5py
scikit-learn
cv2
~~~~



### Train/Validate/Test the OCNet 

We implement training, validating, testing in one script for convenience. You can achieve all the results by runing this script.

~~~~
sh run_asp_oc.sh
~~~~

You are expected to reproduce most of the results provided in our paper.

To achieve the 81.2 on the testing set, you need to train the model with both the training set and validation set for 80,000 iterations first, then you need to finetune this model for 100,000 iterations with fixed learning rate(1e-4). We adopt the online hard example mining accordingly.


## Data preparation

For the cityscapes dataset, please download the dataset from the Cityscapes webset. Unzip all the images under the path "./OCNet/dataset/cityscapes". Ensure the path tree like below within the folder "./OCNet/dataset/cityscapes".

```
|-- README
|-- get_cs_extra.sh
|-- gtCoarse
|   |-- README
|   |-- license.txt
|   |-- train
|   |-- train_extra
|   `-- val
|-- gtFine
|   |-- README
|   |-- license.txt
|   |-- test
|   |-- train
|   `-- val
|-- leftImg8bit
|   |-- README
|   |-- license.txt
|   |-- test
|   |-- train
|   |-- train_extra
|   `-- val
|-- license.txt
`-- tree.txt
```
## Pretrained Models

Please put the pretrained models under the folder "./OCNet/pretrained_model"

[ImageNet Pretrained ResNet-101](http://sceneparsing.csail.mit.edu/model/pretrained_resnet/resnet101-imagenet.pth)

## Docker with the enviroments

[rainbowsecret/pytorch04:20180719](https://hub.docker.com/r/rainbowsecret/pytorch04/tags/)

## Other problems (Performance gap between the Validation set and Testing set)
We find that the mIoU of the class train is unstable sometimes. For example, we run our code for 5 times, there can exist one time the mIoU for class train is 0.42 while we can get 0.75 for other 4 times.

There also exist some problems about the validation/testing set accuracy gap.
For example, if you run the base-oc method for two times, you can achieve 79.3 and 79.8 mIou on the validation set separately while the testing mIou can be 78.55 and 77.69.
Thus I recommend to you to run our methods for multiple times if you want to achieve good performance on the testing set while our method performs pretty robust on the validation set as the reason of the distribution gaps between the training/validation set and the testing set.



## Thanks to the Third Party Libs
[InplaceABN](https://github.com/mapillary/inplace_abn)

[Non-local_pytorch](https://github.com/AlexHex7/Non-local_pytorch).

[Pytorch-Deeplab](https://github.com/speedinghzl/Pytorch-Deeplab)

[PyTorch-Encoding](https://github.com/zhanghang1989/PyTorch-Encoding)


