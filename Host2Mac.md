ssh是一种网络协议，用于计算机之间的加密登录。


Mac使用ssh登录远端服务器
	ssh username@ip
服务器运行jupyter notebook并设置端口
jupyter notebook --no-browser --port=9999
本地运行查看服务器jupyter notebook的token
jupyter notebook list
本地新开一个terminal映射服务器端口到本地
ssh -N -f -L localhost:9999:localhost:8888 username@ip
注：-N告诉SSH没有命令要被远程执行； -f告诉SSH在后台执行；-L是指定port forwarding的配置，远端端口是9999，本地的端口号的8888。
本地浏览器访问localhost: 8888，复制粘贴token

MAC使用scp实现文件传输：
服务器传输文件到Mac
scp username@ip:/home/username/Desktop/filename /Users/username/Desktop
服务器传输文件夹到Mac
scp -r username@ip:/home/username/Desktop/foldername /Users/username/Desktop

Mac传输文件到服务器
scp/Users/username/Desktop/filename username@ip:/home/username/Desktop
Mac传输文件夹到服务器
scp -r /Users/username/Desktop/foldername username@ip:/home/username/Desktop


