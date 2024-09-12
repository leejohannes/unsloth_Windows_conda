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
## 5. 安装deepspeed，如果没有显存担忧可以不安装
这一步需要`cuda`的驱动
请下载`12.1`版本的，地址如下：<p>
https://developer.nvidia.com/cuda-12-1-0-download-archive?target_os=Windows&target_arch=x86_64&target_version=11&target_type=exe_local <p>
只需要`cuda`下的`runtime`中的`libaraies`和`development`,当然nv显卡驱动之类的我是默认大家都装了的

```bash
$Env:DS_BUILD_OPS = 0 `
pip install deepspeed
```
`PowerShell`中的直接给变量命名还是会报错，因为`setup.py`中写的是从环境变量中获取<p>
除此之外还会有个错误就是0.15.1直接从pip上下来编译的包中缺少bat文件<p>
去这里下载：<p>
https://github.com/microsoft/DeepSpeed/tree/master/bin <p>
如果没有了两个文件内容是一样的，文件名分别是`ds_report.bat`和`deepspeed.bat`
```bash
@echo off
python "%~dp0\ds" %*
```
要保存未安装完的文件使用这个指令,如果你觉得下载并编辑太繁琐，当然你也可以直接跳到[这里](#当然你也可以直接) （下文的 # 当然你也可以直接）
```bash
 pip install deepspeed --no-clean
```
`cd`到`$env:temp`中`pip-XXX`的目录,直到看到目录中有'setup.py'
### 当然你也可以直接
```bash
git clone https://github.com/microsoft/DeepSpeed.git
```
解压缩后，`cd`进入`DeepSpeed`目录，然后再
```bash
 python .\setup.py install
```
### ***补齐torch上的其他功能：***
```bash
pip install torch==2.4.0 torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121
```
