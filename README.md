
# PointNest: Learning Deep Multi-scale Nested Feature Propagation for Semantic Segmentation of 3D Point Clouds

This the code of the 
	
### (1) Setup
This code has been tested with Python 3.5, Tensorflow 1.11, CUDA 9.0 and cuDNN 7.4.1 on Ubuntu 16.04.
 
- Clone the repository 
```
git clone --depth=1 https://github.com/jay-Wan/PointNest && cd PointNest
```
- Setup python environment
```
conda create -n randlanet python=3.5
source activate randlanet
pip install -r helper_requirements.txt
sh compile_op.sh
```

**Update 04/8/2023, pre-trained models and results are available now.** 
You can use the pre-trained models at the link of https://pan.baidu.com/s/1GQeC5emOP3XjVkV3-h4LgA?pwd=2023 
提取码：2023.
Note that, please specify the model path in the main function (e.g., `main_S3DIS_ds.py`) if you want to use the pre-trained model and have a quick try of our PointNest.

### (2) S3DIS
S3DIS dataset can be found 
<a href="https://docs.google.com/forms/d/e/1FAIpQLScDimvNMCGhy_rmBA2gHfDu3naktRm6A8BPwAWWDv-Uhm6Shw/viewform?c=0&w=1">here</a>. 
Download the files named "Stanford3dDataset_v1.2_Aligned_Version.zip". Uncompress the folder and move it to 
`/data/S3DIS`.

- Preparing the dataset:
```
python utils/data_prepare_s3dis.py
```
- Start network training:
```
python main_S3DIS_ds.py
```
- Start 6-fold cross validation:
```
sh jobs_6_fold_cv_s3dis.sh
```
- Move all the generated results (*.ply) in `/test` folder to `/data/S3DIS/results`, calculate the final mean IoU results:
```
python utils/6_fold_cv.py
```

### Acknowledgment
-  Part of our code refers to <a href="https://github.com/jlblancoc/nanoflann">nanoflann</a> library and the the recent work <a href="https://github.com/HuguesTHOMAS/KPConv">KPConv</a>.
-  Part of our code refers to [RandLA-Net: Efficient Semantic Segmentation of Large-Scale Point Clouds](https://github.com/QingyongHu/RandLA-Net) 

