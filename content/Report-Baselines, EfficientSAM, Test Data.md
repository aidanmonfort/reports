---
created: 2026-04-15T13:08
updated: 2026-04-15T13:08
---
---
### EfficientSAM
Model from Meta. [Paper](https://arxiv.org/pdf/2312.00863)

It is essentially the same as the MobileSAM model, but with a Masked Pretraining objective. 

Baseline is trained with the SAM loss(20:1 ratio of Focal Loss and Dice Loss, respectively). 
TverskyFocal+Dice trained with 7:3 TverskyFocal Loss and Dice Loss.
Tversky+Dice trained with 7:3 Tversky Loss and Dice Loss.

Recall:
![[recall.png]]

Precision:
![[precision.png]]

F1:
![[f1.png]]

mIoU:
![[miou.png]]


---
### MobileSAM
Baseline is trained with the SAM loss(20:1 ratio of Focal Loss and Dice Loss, respectively). 

Recall:
![[recall-mobile.png]]

Precision:
![[precision-mobile.png]]


F1:
![[f1-mobile.png]]

mIoU:
![[mIoU-mobile.png]]

---
### Normal SAM
Baseline for SAM models is trained with the 20:1 ratio of Focal loss and Dice loss(from paper). 

TverskyFocal+Dice is trained with 7:3 ratio of TverskyFocal and Dice loss. 

---
#### All Models

Recall:
![[all_recall.png]]

Precision:
![[all_precision.png]]

F1:
![[all-f1.png]]

mIoU:
![[all-mIoU.png]]

---
#### ViT-B Baseline VS TverskyFocal + Dice

mIoU:
![[vit-bmIoU.png]]

f1:
![[vit-bf1.png]]

---
#### ViT-L Baseline VS TverskyFocal + Dice

mIoU:
![[vit-lmIoU.png]]

f1:
![[vit-lf1.png]]

---
#### ViT-H Baseline VS TverskyFocal + Dice



---
### DeepLab

Recall:
![[v3-recall.png]]

Precision:
![[deeplab-precision.png]]

F1:
![[deeplab-f1.png]]

mIoU:
![[deeplab-iou.png]]


---
### Test Results

[Link](https://wandb.ai/amonf003-university-of-california-riverside/test_set?nw=nwuseramonf003)


---
### Thoughts
I think for "framing", the [original paper](https://arxiv.org/pdf/1706.05721) talks about using Tvserky loss for class imbalanced datasets, but I feel like we are using it more for reducing the models bias towards over guessing(kind of same thing but maybe not?).  