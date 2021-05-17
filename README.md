# AlignSeg [pdf](https://arxiv.org/pdf/2003.00872)
Pytorch code for paper entitled *AlignSeg: Feature-Aligned Segmentation Networks*. This is a minimal code to run Alignseg on Cityscape dataset.
Shortly afterwards, the code will be reorganized with MMSegmentation.

## Architecture
![Overview of Alignseg](https://user-images.githubusercontent.com/4509744/118447960-f52c6d80-b723-11eb-8af5-12fdedc13262.png)


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

## Visualization of the offset maps
![Overview of offset maps](https://user-images.githubusercontent.com/4509744/118448066-18571d00-b724-11eb-8d49-382ed9858b83.png)
Some visualization of offsets learned in different aggregation stages on the Cityscapes \emph{val} set. The visualizations of each sample are displayed in two rows. The  image  with  its  ground  truth are given in the first column. The following 4 columns represent the offsets in four AlignFA modules, respectively. The upper row contains the offset maps $\Delta^A$ and the lower row contains the offset maps $\Delta^F$. The 1st AlignFA is closer to the input layer, and the 4th AlignFA is closer to the output layer. 
