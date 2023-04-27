
# 1st Solution in Google Universal Image Embedding

#### Shihao Shao[shaoshihao@pku.edu.cn]<br/>
#### Qinghua Cui[cuiqinghua@bjmu.edu.cn]


1st place code in Google Universal Image Embedding is now avaliable!🔥🔥🔥

If you have any further question, Please kindly e-mail us.

The detailed solution can be found [here](https://www.kaggle.com/competitions/google-universal-image-embedding/discussion/359316).


## UPDATE

4/27/2023: The weights are uploaded. This weights can achieve 0.728/0.732 in private LB and public LB, respectively.
https://www.kaggle.com/datasets/louieshao/guieweights0732

## Data preparation

Please download the following datasets:

[Products-10K](https://products-10k.github.io/) <br/>
[Shopee](https://www.kaggle.com/competitions/shopee-product-matching/data) <br/>
[MET Artwork Dataset](https://www.kaggle.com/competitions/shopee-product-matching/data) <br/>
[Alibaba goods](https://www.kaggle.com/datasets/dschettler8845/the-met-dataset)<br/>
[H&M Personalized Fashion](https://www.kaggle.com/competitions/h-and-m-personalized-fashion-recommendations/data)<br/>
[GPR1200](https://www.kaggle.com/code/vitaliykinakh/gpr1200-benchmark-images-retrieval/data)<br/>
[GLDv2-Full](https://github.com/cvdfoundation/google-landmark)<br/>
[DeepFashion - Consumer-to-shop Clothes Retrieval Benchmark part](http://mmlab.ie.cuhk.edu.hk/projects/DeepFashion.html)<br/>

Place them into ```ROOT_PATH/DATA```, and run:
```
python datasets_processing.py
```

The preprocessed datasets will present in ```ROOT_PATH/data_preprocess```

## Pretrained weights preparation

Put ```vit-h-14-laion2b_s32b_b79k.pth``` into the ```pretrained_weights/```

## Training

Install open_clip_280,
```
cd open_clip_280
pip install -e .
```

Run the following commands in order:

```
python -m torch.distributed.run --nproc_per_node=4 --master_addr 127.0.1.0 --master_port 10000 training*.py
```
where * should end with ``` s*.pth ```, please run from ```s1``` to ```s13```.

Please note that when you finish s9, run:

```
cd open_clip_280_overlap
pip install -e .
```
then run the rest of ```s*```.


