# HarDNet-MSEG: A Simple Encoder-Decoder Polyp Segmentation Neural Network that Achieves over 0.9 Mean Dice and 86 FPS

## Main results
### Performance on Kvasir-SEG reference from > [**Real-Time Polyp Detection, Localisation and Segmentation in Colonoscopy Using Deep Learning**](https://arxiv.org/abs/2011.07631)

| Models       | mIoU   | mDice  | F2-score      |Precision   | Recall   | Overall Acc.| FPS|
| :----------: | :----: | :----: | :-----------: | :--------: | :------------: | :---------------: |:--------------: | 
|U-Net         | 0.471  | 0.597  | 0.598         |0.672       | 0.617| 0.894| 11|


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
A large part of the code is borrowed from PraNet(https://github.com/DengPingFan/PraNet) and Cascaded Partial Decoder(https://github.com/wuzhe71/CPD). Thanks for their wonderful works.
