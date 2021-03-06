# 回收扫描


通过图片视频或者AR识别图片中的商品，并把商品进入快速回收



## 工具


- python
- yolo5


## 安装


使用conda安装


```
conda install --file requirements.txt
```


但是有几个不能直接安装，需要特殊处理一下


1. pytorch
> conda install pytorch torchvision -c pytorch  
2. opencv4
> https://pypi.tuna.tsinghua.edu.cn/simple/opencv-python/ 下载需要的whl
> 我的是mac，python3.8所以下载下面的
> pip install opencv_python-4.5.2.54-cp38-cp38-macosx_10_15_x86_64.whl         
3. thop
> pip install --upgrade git+https://github.com/Lyken17/pytorch-OpCounter.git



## 训练集


给图片打标


![image](./docs/image.jpg)


![label](./docs/label.png)


> 一张图片就配合一张label
> 按照顺序是
> 标签、x、y、width、height



可以使用下面的网站，专门配合打标


https://www.makesense.ai/


最终输出yolo格式


# juypter记事本


## 训练


```py
python train.py --img 640 --batch 16 --epochs 3 --data data/recycle.yaml --hyp data/hyp.scratch.yaml --weights data/model/origin.pt  --cache
```


## 检测


```py
python detect.py --weights data/model/recycle.pt --img 640 --conf 0.25 --source detect/
```