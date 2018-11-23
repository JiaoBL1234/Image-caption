请下载对应的训练数据(ai_challenger_caption_train_20170902.zip)(https://challenger.ai/competition/caption/)。 

```Python
pip install -r requirements.txt
```
- 
```Bash
 python -m visdom.server
```
下载预处理好的[caption.pth](http://pytorch-1252820389.cosbj.myqcloud.com/caption.pth)

也可以自行进行处理，运行 
```Bash
python data_preprocess.py process --annotation-file=/data/annotation.json --max-words=5000
```
feature extracting
```Bash
python feature_extract.py
```

## 4 训练

```Bash
python main.py train 
```
完整的命令行选项：
```Python
    caption_data_path='caption.pth'# 经过预处理后的人工描述信息
    img_path='/home/cy/caption_data/' # 图片保存的原始文件夹
    # img_path='/mnt/ht/aichallenger/raw/ai_challenger_caption_train_20170902/caption_train_images_20170902/'
    img_feature_path = 'results.pth' # 所有图片的features,20w*2048的向量
    scale_size = 300
    img_size = 224
    batch_size=8
    shuffle = True
    num_workers = 4
    rnn_hidden = 256
    embedding_dim = 256
    num_layers = 2
    share_embedding_weights=False
    prefix='checkpoints/caption'#模型保存前缀
    env = 'caption'
    plot_every = 10
    debug_file = '/tmp/debugc'

    model_ckpt = None # 模型断点保存路径
    lr=1e-3
    use_gpu=True
    epoch = 1
    test_img = 'img/example.jpeg' 

```

### 测试&Demo
pretrain-model(http://pytorch-1252820389.file.myqcloud.com/caption_0914_1947),


