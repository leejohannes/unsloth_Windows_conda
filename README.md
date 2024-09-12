https://github.com/unslothai/unsloth<p>
https://hf-mirror.com/madbuda/triton-windows-builds<p>
https://github.com/microsoft/DeepSpeed<p>

# 安装步骤：
根据unsloth-2024.8的conda安装指令改写的powershell下的指令<p>
## 1. 创建env
```bash
conda create -p 'unsloth目录' `
    python=3.11 `
     pytorch-cuda=12.1 `
     pytorch cudatoolkit -c pytorch -c nvidia `
     -y
conda activate 'unsloth目录'
```
## 2. 安装 xformers 
```bash
pip install xformers
```
2024年9月12日目前还是安装的这个文件xformers-0.0.27.post2-cp311-cp311-win_amd64.whl<p>
并且要求torch要降级成2.4.0<p>
## 3. 安装其他包
```bash
pip install --no-deps trl peft accelerate bitsandbytes
```
## 4.安装triton
先去 https://hf-mirror.com/madbuda/triton-windows-builds 下载python3.11下编译出来的windows版本的whl包
cd到下载目录并执行下面的指令安装
```bash
pip install triton-2.1.0-cp311-cp311-win_amd64.whl
```
