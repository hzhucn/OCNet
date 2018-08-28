# OCNet


We will release all of implementation in the future weeks

## Abstract 

The basic goal of scene parsing is to label each pixel in an image with the category of the object it belongs to.
The state-of-the-art methods have exploited the effectiveness of context that is defined over image-level such as the whole image or the sub-regions of multiple scales. Such context is not directly related to the goal of scene parsing.

In this work, we propose the Object Context that captures the context in object-level.
The representation of each pixel's object context is computed by aggregating the features of all the pixels that belong to the same category of the object that the associated pixel belongs to. 
Especially, we employ the self-attention method to learn a pixel-wise attention map that carries the probability of each pixel that it belongs to the same category with the associated pixel.

We further propose the Pyramid Object Context and Atrous Spatial Pyramid Object Context to handle the problem of multi-scales.
Based on the object context, we propose the OCNet and show that OCNet achieves state-of-the-art performance on both Cityscapes benchmark and ADE20K benchmark.


## Experiments
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
DFN  |  CVPR2018  | ResNet-101  |  79.3 
DSSPN | CVPR2018  | ResNet-101  | 77.8 
PSANet |  ECCV2018  | ResNet-101  |  80.1 
DenseASPP  |  CVPR2018  | WideDenseNet-161  |  80.6
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
