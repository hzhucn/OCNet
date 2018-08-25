# OCNet


We will release all of implementation in the future weeks

## Abstract 

Context is essential for various computer vision tasks. 
The state-of-the-art scene parsing methods define the context as the prior of the scene categories (e.g., bathroom, badroom, street).
Such scene context is not suitable for the street scene parsing tasks as most of the scenes are similar. 
In this work, we propose the Object Context that captures the prior of the object's category that the pixel belongs to.
We compute the object context by aggregating all the pixels' features according to a attention map that encodes the probability of each pixel that it belongs to the same category with the associated pixel.


## Experiments
All of our implementation is based on pytorch, OCNet can achieve competitive performance on various benchmarks such as Cityscapes and ADE20K without any bells and whistles.

The current performance on the Cityscapes test set of OCNet trained with only the fine-labeled set,


Method | Conference | Backbone | mIoU(\%) 
---- | --- | --- | --- 
PSP |  CVPR2017  | ResNet-101  |  78.4
PSANet |  ECCV2018  | ResNet-101  |  80.1 
DenseASPP  |  CVPR2018  | WideDenseNet-161  |  80.6
OCNet | - |  ResNet-101 | 81.2


The current performance on the ADE20K validation set of the OCNet


Method | Conference | Backbone | mIoU(\%) 
---- | --- | --- | --- 
PSP |  CVPR2017  | ResNet-101  |  43.29
EncNet |  CVPR2018  | ResNet-101  |  44.65
OCNet | - |  ResNet-101 | 45.08
