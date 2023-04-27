# OD-AT
The official implementation code for the paper "Object Detection with Attribute Tagging Task: Model Design and Evaluation on Agricultural Datasets". **All the code will be submitted after the publication of the paper. If necessary, you can also contact us directly!**



## Installation
This project is based on [mmdetection](https://github.com/open-mmlab/mmdetection) and [mmtracking](https://github.com/open-mmlab/mmtracking). So you can refer to [mmdetection installation docs](https://mmdetection.readthedocs.io/en/3.x/get_started.html) and [mmtracking installation docs](https://github.com/open-mmlab/mmtracking/blob/master/docs/en/install.md) for installation and dataset preparation.

### A from-scratch setup script
Assuming that you already have CUDA 11.3 installed, here is a full script for setting up this project with conda.
```shell
conda create -n open-mmlab python=3.8 -y
conda activate open-mmlab

# install PyTorch and torchvision
conda install pytorch==1.12.1 torchvision==0.13.1 torchaudio==0.12.1 cudatoolkit=11.3 -c pytorch

# install mmcv and mmengine
pip install -U openmim
mim install "mmengine==0.7.2"
mim install "mmcls==1.0.0rc5"
mim install "mmcv==2.0.0rc4"

# For mmdetection
cd mmdetection
pip install -v -e .
# "-v" means verbose, or more output
# "-e" means installing a project in editable mode,
# thus any local modifications made to the code will take effect without reinstallation.

# For mmtracking
# install mmtracking
cd mmtracking
pip install -r requirements/build.txt
pip install -v -e .
pip install git+https://github.com/votchallenge/toolkit.git (optional)
pip install git+https://github.com/JonathonLuiten/TrackEval.git
pip install git+https://github.com/lvis-dataset/lvis-api.git
pip install git+https://github.com/TAO-Dataset/tao.git
```

## Dataset
The dataset is available at [Google Drive](https://drive.google.com/file/d/1bBWajjm_rTDTHDhZzecKMrGgTq0gjP79/view?usp=sharing) 
or [Baidu Drive](https://pan.baidu.com/s/1uzUcogD1UyjY0S9D2EeZSA) (code: All the datasets will be opened after the publication of the paper. If necessary, you can also contact us directly!**) 

If use the dataset, please cite the following paper: 
```bibtex
 (The paper is under review, please contact us first)
```

## Model Configuration File
The model configuration files for our paper are list in [new_tomato_at_mask_rcnn_end](mmdetection%2Fconfigs%2Fnew_tomato_at_mask_rcnn_end) and [masktrack_rcnn_new_ara](mmtracking%2Fconfigs%2Fvis%2Fmasktrack_rcnn_new_ara).

You can find key files for OD-AT R-CNN by checking corresponding config files.

## Test

Step 1: Download the checkpoint file from [Google Drive](https://drive.google.com/file/d/1Yqk5bniHRVWERi9Hxh2GTMH04Xa53tOV/view?usp=sharing) and move to `./`.

Step 2: Download the datasets and unzip to `./data/` .

Step 3: Run the following command to test the model.

```shell
python mmdetection/tools/test.py  \
    mmdetection/configs/new_tomato_at_mask_rcnn_end/11_other/mask-rcnn_new-tomato-at_other_soft-nms.py   \
    checkpoint.pth      \
    --work-dir  work_dirs/mask-rcnn_new-tomato-at_other_soft-nms/test/   \
    --out work_dirs/mask-rcnn_new-tomato-at_other_soft-nms/test/out.pkl   \
    --show-dir show_dir
```


## Acknowledgement
We appreciate the following projects:
- [MMDetection](https://github.com/open-mmlab/mmdetection)
- [MMTracking](https://github.com/open-mmlab/mmtracking)
- [multi-task-learning-example](https://github.com/yaringal/multi-task-learning-example)
