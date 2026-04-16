---
created: 2026-04-02T12:32
updated: 2026-04-02T12:32
featured_image: imgs/Pasted image 20260402123458.png
thumbnail: imgs/resized/1e7116dee3ee769d38e33addf1ace275_86cf658e.webp
---
---

From Last Time, across all experiments, SAM models, TV Loss scales. 

![[Pasted image 20260402123458.png]]

mIoU tends to converge towards .70 at the higher end. 

![[Pasted image 20260402123554.png]]

f1 tends towards .82 at the higher end. 

---
### Clean Data:
---

For all of the data cleaning, I added a road class(28). In the CalCROP21 source code, it's a little weird, but they have 28 listed as one of the class but it does not get used, and 100 is instead used for the Unknown class. 

This was the best performing tile for default SAM. 
![[T11SKA_2018_9_4_comparison.png]]

This is the poorly performing tile that we normally focus on.
![[T11SKV_2018_5_4_comparison.png]]

#### General Stats:
---
[Link](https://docs.google.com/spreadsheets/d/1eF4us4tGBlhfzO66XEW62nvMq70GKZ3mUV3SgmpJEac/edit?usp=sharing)

![[Pasted image 20260402123903.png]]

![[Pasted image 20260402123918.png]]

### Visualization GT Mask Changes
---
![[Pasted image 20260402130635.png]]

**VS:**

![[Pasted image 20260402130705.png]]

Question: Soft label updates around roads?

# MobileSAM Experiments:
---
- Batch size 16
- Full model finetuning
- 50 Epochs(With Early Stopping)
- LR: 5e-5
- TV: 5e-3
- $\mathcal{L} = 0.7\text{TverskyFocal}(\gamma = 2.0, \alpha = 0.7, \beta = 0.3) + 0.3\text{DiceLoss}$
- WD: 0.01
- Tried both cleaned/uncleaned data

![[Pasted image 20260402131252.png]]

![[Pasted image 20260402131316.png]]


[Link](https://wandb.ai/amonf003-university-of-california-riverside/mobile/runs/vt6lrjjg/panel/jeq824qci)

### DeepLab:
---
- Full model finetuning
- 50 Epochs(With Early Stopping)
- LR: 5e-5
- TV: 5e-3
- $\mathcal{L} = 0.7\text{TverskyFocal}(\gamma = 2.0, \alpha = 0.7, \beta = 0.3) + 0.3\text{DiceLoss}$
- WD: 0.01
- Only Cleaned Labels

#### V3
---
[Paper](https://arxiv.org/pdf/1706.05587)
Batch Size: 4

![[Pasted image 20260402131929.png]]

![[Pasted image 20260402131946.png]]

[Link](https://wandb.ai/amonf003-university-of-california-riverside/deeplab/runs/yqbg45yc?nw=nwuseramonf003)

#### V3+
---
[Paper](https://arxiv.org/pdf/1802.02611)
Batch Size: 8

![[Pasted image 20260402132439.png]]

![[Pasted image 20260402132506.png]]

[Link](https://wandb.ai/amonf003-university-of-california-riverside/deeplab/runs/6wygr3gc?nw=nwuseramonf003)

### Todo:
---
- Test Results
- Finetune Encoder(Full SAM)
- Out-of-the-box MobileSAM + DeepLab
- Paper Writing
- Knowledge Distillation


### Some Other Thoughts:
---

![[Pasted image 20260402134842.png]]

From CalCROP paper. Is it better to train on CDL(Noisy Grids) with higher TV loss added to address, or train on CalCROP(model generated grids that predict CDL grids)

