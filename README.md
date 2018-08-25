# OCNet
We will release all of implementation in the future weeks


All of our implementation is based on pytorch, PGCNet can achieve competitive performance on various benchmarks such as Cityscapes and ADE20K without any bells and whistles.


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
