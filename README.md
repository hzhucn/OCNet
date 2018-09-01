# OCNet


We will release all of implementation in the future weeks

## Abstract 

Context is essential for various computer vision tasks.
The state-of-the-art scene parsing methods have exploited the effectiveness of the context defined over image-level.
Such context carries the mixture of objects belonging to different categories.

According to that the label of each pixel is defined as the category of the object it belongs to, we propose the Object Context that considers the objects belonging to the same category. 
The representation of any pixel P's object context is the aggregation of all the pixels' features that belong to the same category with P.
Since it is impractical to estimate all the objects belonging to the same category in advance,
we employ the self-attention method to approximate the objects by learning a pixel-wise similarity map.

We further propose the Pyramid Object Context and Atrous Spatial Pyramid Object Context to capture context of multiple scales.
Based on the object context, we introduce the OCNet and show that OCNet achieves state-of-the-art performance on both Cityscapes benchmark and ADE20K benchmark.


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
