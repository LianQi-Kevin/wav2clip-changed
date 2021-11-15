## 在Win10上使用wav2clip
### 使用cuda11.1和cudnn11.2
### 原项目为：https://github.com/descriptinc/lyrebird-wav2clip

##### 1. 首先创建conda环境
```
conda creat -n wav2clip python=3.8
```
##### 2. 安装torch==1.9 torchvision==0.10 torchaudio==0.9
```
pip install torch==1.9.0+cu111 torchvision==0.10.0+cu111 torchaudio==0.9.0 -f https://download.pytorch.org/whl/torch_stable.html
```

##### 3. 安装 pywin32==301 替换掉默认的pywin32==302
```
pip uninstall pywin32
pip install pywin32==301
```

##### 4. 安装CLIP

```
# https://github.com/openai/CLIP
pip install git+https://github.com/openai/CLIP.git
```

##### 5. 直接clone修改好的存储库
```
git clone https://github.com/LianQi-Kevin/wav2clip-changed.git
```

##### 6. 安装剩余库
```
cd lyrebird-wav2clip
pip install -r requirement.txt
```

##### 7. 修改VQGAN-CLIP/main.py中的audio_file变量 设定为自己的wav文件

-----------------
#### 从原始库clone并创建wav2clip 
#### 替换掉上面的5.和 6.
##### 5. clone存储库并替换文件
```
git clone https://github.com/descriptinc/lyrebird-wav2clip.git
cd lyrebird-wav2clip
git clone https://github.com/nerdyrodent/VQGAN-CLIP
mv VQGAN-CLIP/generate.py VQGAN-CLIP/generate_bk.py
cp scripts/VQGAN-CLIP/main.py /VQGAN-CLIP/main.py
cp scripts/VQGAN-CLIP/generate.py VQGAN-CLIP/generate.py
```

##### 6. 下载模型
```
cd VQGAN-CLIP/
mkdir checkpoints
curl -L -o checkpoints/vqgan_imagenet_f16_16384.yaml -C - 'https://heibox.uni-heidelberg.de/d/a7530b09fed84f80a887/files/?p=%2Fconfigs%2Fmodel.yaml&dl=1'
curl -L -o checkpoints/vqgan_imagenet_f16_16384.ckpt -C - 'https://heibox.uni-heidelberg.de/d/a7530b09fed84f80a887/files/?p=%2Fckpts%2Flast.ckpt&dl=1'
```



