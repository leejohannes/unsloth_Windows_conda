https://github.com/unslothai/unsloth<p>
https://hf-mirror.com/madbuda/triton-windows-builds<p>
https://github.com/microsoft/DeepSpeed<p>

安装步骤：<p>
根据unsloth-2024.8的conda安装指令改写的powershell下的指令<p>
[code]conda create -p 'unsloth目录' `
    python=3.11 `
     pytorch-cuda=12.1 `
     pytorch cudatoolkit -c pytorch -c nvidia `
     -y
conda activate 'unsloth目录'[/code]
