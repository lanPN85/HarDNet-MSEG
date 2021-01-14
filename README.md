# HarDNet-MSEG: An Efficient Network for Polyp Segmentation


### 1. Training/Testing


1. Environment setting (Prerequisites):
    
    + Creating a virtual environment in terminal: `conda create -n *your_env_name* python=3.6`.
    
    + Installing necessary packages: PyTorch 1.1

2. Downloading necessary data:

    + downloading testing dataset and move it into `./data/TestDataset/`, 
    which can be found in this [download link (Google Drive)](https://drive.google.com/file/d/1o8OfBvYE6K-EpDyvzsmMPndnUMwb540R/view?usp=sharing).
    
    + downloading training dataset and move it into `./data/TrainDataset/`, 
    which can be found in this [download link (Google Drive)](https://drive.google.com/file/d/1lODorfB33jbd-im-qrtUgWnZXxB94F55/view?usp=sharing).
   
3. Training :
    
    Just simply change the --train_path & --test_path in Train.py
    And just run the Train.py

4. Testing & inference result :

    Just simply change the data_path in Test.py (line 16)
    And you can get the inference results in results/
    

### 2 Evaluating your trained model:

Change the image_root, gt_root in line 49, 50 in eval_Kvasir.py
Then run the eval_Kvasir.py to get a similar result to our report for Kvasir Dataset.

Another one is written in MATLAB code ([link](https://drive.google.com/file/d/1_h4_CjD5GKEf7B1MRuzye97H0MXf2GE9/view?usp=sharing)).
You can see how to run it in https://github.com/DengPingFan/PraNet#32-evaluating-your-trained-model-

### 3 Acknowledgement
A large part of the code is borrowed from PraNet(https://github.com/DengPingFan/PraNet) and Cascaded Partial Decoder(https://github.com/wuzhe71/CPD). Thanks for their wonderful works.
