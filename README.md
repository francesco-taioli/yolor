# YOLOR
implementation of paper - [You Only Learn One Representation: Unified Network for Multiple Tasks](https://arxiv.org/abs/2105.04206)

[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/you-only-learn-one-representation-unified/real-time-object-detection-on-coco)](https://paperswithcode.com/sota/real-time-object-detection-on-coco?p=you-only-learn-one-representation-unified)

![Unified Network](https://github.com/WongKinYiu/yolor/blob/main/figure/unifued_network.png)

<img src="https://github.com/WongKinYiu/yolor/blob/main/figure/performance.png" height="480">

To reproduce the results in the paper, please use [this branch](https://github.com/WongKinYiu/yolor/tree/paper).

| Model | Test Size | AP<sup>test</sup> | AP<sub>50</sub><sup>test</sup> | AP<sub>75</sub><sup>test</sup> | AP<sub>S</sub><sup>test</sup> | AP<sub>M</sub><sup>test</sup> | AP<sub>L</sub><sup>test</sup> | batch1 throughput |
| :-- | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | 
| **YOLOR-P6** | 1280 | **52.6%** | **70.6%** | **57.6%** | **34.7%** | **56.6%** | **64.2%** | 49 *fps* |
| **YOLOR-W6** | 1280 | **54.1%** | **72.0%** | **59.2%** | **36.3%** | **57.9%** | **66.1%** | 47 *fps* |
| **YOLOR-E6** | 1280 | **54.8%** | **72.7%** | **60.0%** | **36.9%** | **58.7%** | **66.9%** | 37 *fps* |
| **YOLOR-D6** | 1280 | **55.4%** | **73.3%** | **60.6%** | **38.0%** | **59.2%** | **67.1%** | 30 *fps* |
|  |  |  |  |  |  |  |
| **YOLOv4-P5** | 896 | **51.8%** | **70.3%** | **56.6%** | **33.4%** | **55.7%** | **63.4%** | 41 *fps* |
| **YOLOv4-P6** | 1280 | **54.5%** | **72.6%** | **59.8%** | **36.6%** | **58.2%** | **65.5%** | 30 *fps* |
| **YOLOv4-P7** | 1536 | **55.5%** | **73.4%** | **60.8%** | **38.4%** | **59.4%** | **67.7%** | 16 *fps* |
|  |  |  |  |  |  |  |

To reproduce the inference speed, please see [darknet](https://github.com/WongKinYiu/yolor/tree/main/darknet).

| Model | Test Size | AP<sup>val</sup> | AP<sub>50</sub><sup>val</sup> | AP<sub>75</sub><sup>val</sup> | AP<sub>S</sub><sup>val</sup> | AP<sub>M</sub><sup>val</sup> | AP<sub>L</sub><sup>val</sup> | batch1 throughput |
| :-- | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | 
| [**YOLOv4-CSP**](/cfg/yolov4_csp.cfg) | 640 | **49.1%** | **67.7%** | **53.8%** | **32.1%** | **54.4%** | **63.2%** | 76 *fps* |
| [**YOLOR-CSP**](/cfg/yolor_csp.cfg) | 640 | **49.2%** | **67.6%** | **53.7%** | **32.9%** | **54.4%** | **63.0%** | [weights](https://drive.google.com/file/d/1ZEqGy4kmZyD-Cj3tEFJcLSZenZBDGiyg/view?usp=sharing) |
| [**YOLOR-CSP***](/cfg/yolor_csp.cfg) | 640 | **50.0%** | **68.7%** | **54.3%** | **34.2%** | **55.1%** | **64.3%** | [weights](https://drive.google.com/file/d/1OJKgIasELZYxkIjFoiqyn555bcmixUP2/view?usp=sharing) |
|  |  |  |  |  |  |  |
| [**YOLOv4-CSP-X**](/cfg/yolov4_csp_x.cfg) | 640 | **50.9%** | **69.3%** | **55.4%** | **35.3%** | **55.8%** | **64.8%** | 53 *fps* |
| [**YOLOR-CSP-X**](/cfg/yolor_csp_x.cfg) | 640 | **51.1%** | **69.6%** | **55.7%** | **35.7%** | **56.0%** | **65.2%** | [weights](https://drive.google.com/file/d/1L29rfIPNH1n910qQClGftknWpTBgAv6c/view?usp=sharing) |
| [**YOLOR-CSP-X***](/cfg/yolor_csp_x.cfg) | 640 | **51.5%** | **69.9%** | **56.1%** | **35.8%** | **56.8%** | **66.1%** | [weights](https://drive.google.com/file/d/1NbMG3ivuBQ4S8kEhFJ0FIqOQXevGje_w/view?usp=sharing) |
|  |  |  |  |  |  |  |

Developing...

| Model | Test Size | AP<sup>test</sup> | AP<sub>50</sub><sup>test</sup> | AP<sub>75</sub><sup>test</sup> | AP<sub>S</sub><sup>test</sup> | AP<sub>M</sub><sup>test</sup> | AP<sub>L</sub><sup>test</sup> |
| :-- | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| **YOLOR-CSP** | 640 | **50.7%** | **69.2%** | **55.2%** | **31.2%** | **55.0%** | **63.6%** |

## Installation

Docker environment (recommended)
<details><summary> <b>Expand</b> </summary>

```
# create the docker container, you can change the share memory size if you have more.
nvidia-docker run --name yolor -it -v your_coco_path/:/coco/ -v your_code_path/:/yolor --shm-size=64g nvcr.io/nvidia/pytorch:20.11-py3

# apt install required packages
apt update
apt install -y zip htop screen libgl1-mesa-glx

# pip install required packages
pip install seaborn thop

# install mish-cuda if you want to use mish activation
# https://github.com/thomasbrandon/mish-cuda
# https://github.com/JunnYu/mish-cuda
cd /
git clone https://github.com/JunnYu/mish-cuda
cd mish-cuda
python setup.py build install

# install pytorch_wavelets if you want to use dwt down-sampling module
# https://github.com/fbcotter/pytorch_wavelets
cd /
git clone https://github.com/fbcotter/pytorch_wavelets
cd pytorch_wavelets
pip install .

# go to code folder
cd /yolor
```

</details>

Colab environment
<details><summary> <b>Expand</b> </summary>
  
```
git clone https://github.com/WongKinYiu/yolor
cd yolor

# pip install required packages
pip install -qr requirements.txt

# install mish-cuda if you want to use mish activation
# https://github.com/thomasbrandon/mish-cuda
# https://github.com/JunnYu/mish-cuda
git clone https://github.com/JunnYu/mish-cuda
cd mish-cuda
python setup.py build install
cd ..

# install pytorch_wavelets if you want to use dwt down-sampling module
# https://github.com/fbcotter/pytorch_wavelets
git clone https://github.com/fbcotter/pytorch_wavelets
cd pytorch_wavelets
pip install .
cd ..
```

</details>

Prepare COCO dataset
<details><summary> <b>Expand</b> </summary>

```
cd /yolor
bash scripts/get_coco.sh
```

</details>

Prepare pretrained weight
<details><summary> <b>Expand</b> </summary>

```
cd /yolor
bash scripts/get_pretrain.sh
```

</details>

## Testing

[`yolor_p6.pt`](https://drive.google.com/file/d/1Tdn3yqpZ79X7R1Ql0zNlNScB1Dv9Fp76/view?usp=sharing)

```
python test.py --data data/coco.yaml --img 1280 --batch 32 --conf 0.001 --iou 0.65 --device 0 --cfg cfg/yolor_p6.cfg --weights yolor_p6.pt --name yolor_p6_val
```

You will get the results:

```
 Average Precision  (AP) @[ IoU=0.50:0.95 | area=   all | maxDets=100 ] = 0.52510
 Average Precision  (AP) @[ IoU=0.50      | area=   all | maxDets=100 ] = 0.70718
 Average Precision  (AP) @[ IoU=0.75      | area=   all | maxDets=100 ] = 0.57520
 Average Precision  (AP) @[ IoU=0.50:0.95 | area= small | maxDets=100 ] = 0.37058
 Average Precision  (AP) @[ IoU=0.50:0.95 | area=medium | maxDets=100 ] = 0.56878
 Average Precision  (AP) @[ IoU=0.50:0.95 | area= large | maxDets=100 ] = 0.66102
 Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets=  1 ] = 0.39181
 Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets= 10 ] = 0.65229
 Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets=100 ] = 0.71441
 Average Recall     (AR) @[ IoU=0.50:0.95 | area= small | maxDets=100 ] = 0.57755
 Average Recall     (AR) @[ IoU=0.50:0.95 | area=medium | maxDets=100 ] = 0.75337
 Average Recall     (AR) @[ IoU=0.50:0.95 | area= large | maxDets=100 ] = 0.84013
```

## Training

Single GPU training:

```
python train.py --batch-size 8 --img 1280 1280 --data coco.yaml --cfg cfg/yolor_p6.cfg --weights '' --device 0 --name yolor_p6 --hyp hyp.scratch.1280.yaml --epochs 300
```

Multiple GPU training:

```
python -m torch.distributed.launch --nproc_per_node 2 --master_port 9527 train.py --batch-size 16 --img 1280 1280 --data coco.yaml --cfg cfg/yolor_p6.cfg --weights '' --device 0,1 --sync-bn --name yolor_p6 --hyp hyp.scratch.1280.yaml --epochs 300
```

Training schedule in the paper:

```
python -m torch.distributed.launch --nproc_per_node 8 --master_port 9527 train.py --batch-size 64 --img 1280 1280 --data data/coco.yaml --cfg cfg/yolor_p6.cfg --weights '' --device 0,1,2,3,4,5,6,7 --sync-bn --name yolor_p6 --hyp hyp.scratch.1280.yaml --epochs 300
python -m torch.distributed.launch --nproc_per_node 8 --master_port 9527 tune.py --batch-size 64 --img 1280 1280 --data data/coco.yaml --cfg cfg/yolor_p6.cfg --weights 'runs/train/yolor_p6/weights/last_298.pt' --device 0,1,2,3,4,5,6,7 --sync-bn --name yolor_p6-tune --hyp hyp.finetune.1280.yaml --epochs 450
python -m torch.distributed.launch --nproc_per_node 8 --master_port 9527 train.py --batch-size 64 --img 1280 1280 --data data/coco.yaml --cfg cfg/yolor_p6.cfg --weights 'runs/train/yolor_p6-tune/weights/epoch_424.pt' --device 0,1,2,3,4,5,6,7 --sync-bn --name yolor_p6-fine --hyp hyp.finetune.1280.yaml --epochs 450
```

## Inference

[`yolor_p6.pt`](https://drive.google.com/file/d/1Tdn3yqpZ79X7R1Ql0zNlNScB1Dv9Fp76/view?usp=sharing)

```
python detect.py --source inference/images/horses.jpg --cfg cfg/yolor_p6.cfg --weights yolor_p6.pt --conf 0.25 --img-size 1280 --device 0
```

You will get the results:

![horses](https://github.com/WongKinYiu/yolor/blob/main/inference/output/horses.jpg)

## Citation

```
@article{wang2021you,
  title={You Only Learn One Representation: Unified Network for Multiple Tasks},
  author={Wang, Chien-Yao and Yeh, I-Hau and Liao, Hong-Yuan Mark},
  journal={arXiv preprint arXiv:2105.04206},
  year={2021}
}
```

## Acknowledgements

<details><summary> <b>Expand</b> </summary>

* [https://github.com/AlexeyAB/darknet](https://github.com/AlexeyAB/darknet)
* [https://github.com/WongKinYiu/PyTorch_YOLOv4](https://github.com/WongKinYiu/PyTorch_YOLOv4)
* [https://github.com/WongKinYiu/ScaledYOLOv4](https://github.com/WongKinYiu/ScaledYOLOv4)
* [https://github.com/ultralytics/yolov3](https://github.com/ultralytics/yolov3)
* [https://github.com/ultralytics/yolov5](https://github.com/ultralytics/yolov5)

</details>
