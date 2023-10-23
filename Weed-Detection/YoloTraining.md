# YOLOV4 Trainning for Weed Detection For Sesame Crop 
> Run In colab for faster and easy Training

Install kaggle for the datase and YOLOv4 for Model And the needed dependencies

```
!pip install kaggle
!git clone https://github.com/ultralytics/yolov5  # clone repo
%cd yolov5
!git reset --hard 064365d8683fd002e9ad789c1e91fa3d021b44f0
!pip install -qr requirements.txt  # install dependencies (ignore errors)
```
Import pytorch for training 
```
import torch

from IPython.display import Image, clear_output  # to display images
from utils.downloads import attempt_download  # to download models/datasets
```
Downloading Dataset
```
! mkdir ~/.kaggle
! cp /content/drive/MyDrive/kaggle.json ~/.kaggle/kaggle.json
! chmod 600 ~/.kaggle/kaggle.json
! kaggle datasets download ravirajsinh45/crop-and-weed-detection-data-with-bounding-boxes
! unzip crop-and-weed-detection-data-with-bounding-boxes.zip
```
Chech the details and change the necessary
```
%cat /content/yolov5/models/yolov5n.yaml
```
```
%%time
%cd /content/yolov5/
```
Train Yolo model 
```
!python train.py --img 512 --batch 16 --epochs 100 --data '../data.yaml' --cfg /content/yolov5/models/yolov5n.yaml --weights '' --name yolov5n_results  --cache
```

See The Test results
```
# first, display our ground truth data
print("GROUND TRUTH TEST DATA:")
Image(filename='/content/yolov5/runs/train/yolov5n_results/train_batch0.jpg', width=1080)
Image(filename='/content/yolov5/runs/train/yolov5n_results/train_batch1.jpg', width=1080)
Image(filename='/content/yolov5/runs/train/yolov5n_results/train_batch2.jpg', width=1080)
```
