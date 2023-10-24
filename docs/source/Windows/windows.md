# Windows优化
## c盘存储优化
- 取消错误信息日志
![](./dumpcrash.png)
- 移动桌面，下载，文档等库的文件夹位置到其他盘
- pip 缓存目录
``` bash
pip config set global.cache-dir "E:/pipcache"
```
- conda 缓存目录以及默认envs目录设置

.condarc文件内容
``` bash
channels:
  - defaults
  - conda-forge
show_channel_urls: true
default_channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
custom_channels:
  conda-forge: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  msys2: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  bioconda: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  menpo: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch-lts: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  simpleitk: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
pkgs_dirs:
  - E:\condacache
  - C:\Users\x\miniconda3\pkgs
  - C:\Users\x\.conda\pkgs
  - C:\Users\x\AppData\Local\conda\conda\pkgs
envs_dirs:
  - E:\PythonCode
  - C:\Users\x\miniconda3\envs
  - C:\Users\x\.conda\envs
  - C:\Users\x\AppData\Local\conda\conda\envs
```