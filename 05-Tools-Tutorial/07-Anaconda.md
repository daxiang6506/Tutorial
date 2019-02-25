# ANACONDA3

## 命令

* install

```bash
chmod +x ./Anaconda3-2018.12-Linux-x86_64.sh
./Anaconda3-2018.12-Linux-x86_64.sh
source ~/.bashrc
conda update -n base conda
conda create --name log-tools python=3.6
conda activate log-tools
conda install --yes --file requirements.txt
```

```bash
pyqt5 pyqt5-sip pyqtgraph pygame paramiko
vim requirements.txt
pip install -r requirements.txt
```

```bash
Linux
修改 ~/.pip/pip.conf (没有就创建一个)， 修改 index-url至tuna，内容如下：

[global]
 index-url = https://pypi.tuna.tsinghua.edu.cn/simple
```

```bash
/home/roaddb/others/lijian/localizationLogTools
python3 mainCaseRun.py
python3 mainLog.py
```

```bash
conda env list
conda create -n your_env_name python=X.X
source activate your_env_name
source deactivate base
```
