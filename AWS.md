# Macbook运行AWS EC2 Ubuntu，安装GPU和Python

我选择的地区是Virginia，GPU是p2.xlarge。  
下载key是一个.dem文件，要保存好。  
申请instance，建议申请p2.xlarge。p3等了一天还没通过。通过后会发邮件通知。  
登录，运行时内存改成20g要不然内存不够用。  

## connect
按照指示运行ubuntu  
chmod 400 qiaoVirginia.pem  
ssh -i "qiaoVirginia.pem" ubuntu@ec2-34-229-91-157.compute-1.amazonaws.com  

## 安装编译器和git
sudo apt-get install build-essential git

## 安装cuda
wget http://developer.download.nvidia.com/compute/cuda/10.1/Prod/local_installers/cuda_10.1.243_418.87.00_linux.run  
sudo sh cuda_10.1.243_418.87.00_linux.run  

查看本地gpu：nvidia-smi  

vim ~/.bashrc  
Export LD_LIBRARY_PATH PATH=$LD_LIBRARY_PATH:/usr/local/cuda-10.1/lib64  
bash  

## 安装python3
sudo apt-get install python3  
安装虚拟环境  
sudo pip3 install virtualenv  
建立虚拟环境  
virtualenv venv  
source venv/bin/activate  
deactivate  

删除虚拟环境：  
sudo rm -rf venv  

## 安装jupyter
pip3 install jupyter

To be able to run jupyter notebook from terminal, you need to make sure that ~/.local/bin is in your path.  
Do this by running export PATH=$PATH:~/.local/bin


## 映射jupyter notebook端口
打开一个新的terminal：  
ssh -i "qiaoVirginia.pem" -L 8888:localhost:8888 ubuntu@ec2-34-229-91-157.compute-1.amazonaws.com  
在浏览器中输入localhost:8888  

## 下次登录
连接服务器后，激活环境：  
source venv/bin/activate  
启动 jupyter notebook：  
jupyter notebook --ip=0.0.0.0  
在浏览器中输入localhost:8888  

## 一些可能有用的小命令
用如下命令可以查看当前环境安装了哪些包：
$ pip freeze

查看占用端口 lsof -i  
关闭占用端口 kill -9 PID

