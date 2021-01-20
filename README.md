# HarDNet-MSEG: A Simple Encoder-Decoder Polyp Segmentation Neural Network that Achieves over 0.9 Mean Dice and 86 FPS

> [**HarDNet-MSEG: A Simple Encoder-Decoder Polyp Segmentation Neural Network that Achieves over 0.9 Mean Dice and 86 FPS**](https://arxiv.org/abs/2101.07172)

> [**HarDNet: A Low Memory Traffic Network**](https://arxiv.org/abs/1909.00948)

## Main results
### Performance on Kvasir-SEG reference from > [**Real-Time Polyp Detection, Localisation and Segmentation in Colonoscopy Using Deep Learning**](https://arxiv.org/abs/2011.07631) ( FPS meansures on 2080Ti )

| Models       | mIoU   | mDice  | F2-score      |Precision   | Recall   | Overall Acc.| FPS|
| :----------: | :----: | :----: | :-----------: | :--------: | :------------: | :---------------: |:--------------: | 
|U-Net         | 0.471  | 0.597  | 0.598         |0.672       | 0.617| 0.894| 11|
|ResUNet |0.572| 0.690 |0.699 |0.745| 0.725| 0.917| 15|
|DoubleUNet |0.733| 0.813 |0.820 |0.861 |0.840 |0.949 |7.5|
|DeepLabv3+[ResNet50] |0.776| 0.857 |0.855 |0.891| 0.8616 |0.961 |28|
|U-Net[ResNet34]| 0.810 |0.876| 0.862 |**0.944**| 0.860 |0.968| 35|
|**HarDNet-MSEG** |**0.848**   |  **0.904**| **0.915**| 0.907| **0.923**| **0.969**|**86.7**|

### Performance on Kvasir-SEG reference from another training split > [**PraNet: Parallel Reverse Attention Network for Polyp Segmentation**](https://arxiv.org/abs/2006.11392)( FPS meansures on 2080Ti )

| Models       | mDice   | mIoU  | wfm      |Sm   | MAE   | maxEm | FPS|
| :----------: | :----: | :----: | :-----------: | :--------: | :------------: | :---------------: |:--------------: | 
|U-Net         | 0.818  | 0.746  | 0.794         |0.858       | 0.055| 0.893| 11|
|U-Net++ |0.821 |0.743 |0.808 |0.862 |0.048 |0.910| 25|
|SFA |0.723| 0.611| 0.67| 0.782 |0.075 |0.849| 40|
|PraNet |0.898 |0.840| 0.885| 0.915| 0.030| 0.948| 66|
|[**HarDNet-MSEG**](https://drive.google.com/file/d/1nj-zv64RiWwYjCmWg4NME7HNf_nBncUu/view?usp=sharing) |**0.912**| **0.857**| **0.903**| **0.923** |**0.025**|**0.958** |**88**|

###  Inference results of Kvasir-SEG compare with PraNet
![](inf.png =80%x)

## Installation & Usage
### 1. Training/Testing


1. Environment setting (Prerequisites):
    
    + `conda create -n *your_env_name* python=3.6`.
    
    + Then install PyTorch 1.1.

2. Downloading necessary data:
    
    + downloading testing dataset and move it into your test_path
    which can be found in this [download link (Google Drive)](https://drive.google.com/file/d/1o8OfBvYE6K-EpDyvzsmMPndnUMwb540R/view?usp=sharing).
    
    + downloading training dataset and move it into your train_path
    which can be found in this [download link (Google Drive)](https://drive.google.com/file/d/1lODorfB33jbd-im-qrtUgWnZXxB94F55/view?usp=sharing).
   
3. Training :

    First download pretrain_weight : hardnet68.pth for HarDNet68 in https://github.com/PingoLH/Pytorch-HarDNet
    
    And change the weight path in lib/hardnet_68.py line 203
    
    Then Just simply change the --train_path & --test_path in Train.py
    
    Final step is to run the Train.py

4. Testing & inference result :

    Just simply change the data_path in Test.py (line 16)
    
    Here is the weight we using on the report https://drive.google.com/file/d/1nj-zv64RiWwYjCmWg4NME7HNf_nBncUu/view?usp=sharing
    
    Download it, and run "python Test.py --pth_path 'path of the weight' "
    
    And you can get the inference results in results/
    

### 2 Evaluating your trained model:

Change the image_root, gt_root in line 49, 50 in eval_Kvasir.py
Then run the eval_Kvasir.py to get a similar result (about +0.002) to our report for Kvasir Dataset.

Another one is written in MATLAB code ([link](https://drive.google.com/file/d/1_h4_CjD5GKEf7B1MRuzye97H0MXf2GE9/view?usp=sharing)).
You can see how to run it in https://github.com/DengPingFan/PraNet#32-evaluating-your-trained-model-
And our report is using this code to evaluate.

### 3 Acknowledgement

A large part of the code is borrowed from 
PraNet(https://github.com/DengPingFan/PraNet) 
Cascaded Partial Decoder(https://github.com/wuzhe71/CPD). 

Thanks for their wonderful works.

## Citation

      @misc{huang2021hardnetmseg,
      title={HarDNet-MSEG: A Simple Encoder-Decoder Polyp Segmentation Neural Network that Achieves over 0.9 Mean Dice and 86 FPS}, 
      author={Chien-Hsiang Huang and Hung-Yu Wu and Youn-Long Lin},
      year={2021},
      eprint={2101.07172},
      archivePrefix={arXiv},
      primaryClass={cs.CV}
      } 
      
      @inproceedings{chao2019hardnet,
      title={Hardnet: A low memory traffic network},
      author={Chao, Ping and Kao, Chao-Yang and Ruan, Yu-Shan and Huang, Chien-Hsiang and Lin, Youn-Long},
      booktitle={Proceedings of the IEEE International Conference on Computer Vision},
      pages={3552--3561},
      year={2019}
      }
