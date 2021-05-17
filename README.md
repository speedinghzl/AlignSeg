# AlignSeg [pdf](https://arxiv.org/pdf/2003.00872)
Pytorch code for paper entitled *AlignSeg: Feature-Aligned Segmentation Networks*. This is a minimal code to run Alignseg on Cityscape dataset.
Shortly afterwards, the code will be reorganized with MMSegmentation.


### Requirements && Install
Python 3.7

2 x 32g GPUs (e.g. TITAN XP)

```bash
# Install **Apex**
$ git clone https://github.com/NVIDIA/apex
$ cd apex
$ pip install -v --no-cache-dir --global-option="--cpp_ext" --global-option="--cuda_ext" ./

# Install **Inplace-ABN**
$ git clone https://github.com/mapillary/inplace_abn.git
$ cd inplace_abn
$ python setup.py install
```

### Dataset and pretrained model

Plesae download cityscapes dataset and unzip the dataset into `YOUR_CS_PATH`.

Please download MIT imagenet pretrained [resnet101-imagenet.pth](https://drive.google.com/file/d/19rro_8KaQeJY4kW6FMlase5ywn0p6bII/view?usp=sharing), and put it into `dataset` folder.

### Training and Evaluation
```bash
./run_local.sh YOUR_CS_PATH alignseg 120000 872,872 1
``` 

### Models

| **OHEM** | **mIOU on cityscape val set (single scale)**           | **Link** |
|:-------:|:---------------------:|:---------:|
| NO | 80.3 | [model](https://drive.google.com/file/d/1bq235SNBWfZb_8bWbWDovBqbEQEZZneW/view?usp=sharing) |
| YES | 81.4 | [model](https://drive.google.com/file/d/12lqI6FBOVnl9L28ofl_2UHMCKyvrt8A9/view?usp=sharing) |

### Citing

If you find this code useful in your research, please consider citing:

    @ARTICLE{alignseg,
        title={Alignseg: Feature-aligned segmentation networks},
        author={Huang, Zilong and Wei, Yunchao and Wang, Xinggang and Liu, Wenyu and Huang, Thomas S and Shi, Honghui},
        journal={IEEE Transactions on Pattern Analysis and Machine Intelligence},
        year={2021},
        volume={},
        number={},
        pages={1-1},
        doi={10.1109/TPAMI.2021.3062772}
    }
