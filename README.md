https://github.com/unslothai/unsloth<p>
https://hf-mirror.com/madbuda/triton-windows-builds<p>
https://github.com/microsoft/DeepSpeed<p>

### 安装步骤：
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
2024年9月12日目前还是安装的这个文件xformers-0.0.27.post2-cp311-cp311-win_amd64.whl[p]
