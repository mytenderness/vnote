# tf

```txt
环境要求
- 安装好 hygon4.5.2-V01.4 软件栈包括内核驱动和用户态文件
- 保持网络连接，安装过程中python 需要下载依赖库
OS 依赖库
Centos7.6:
- yum install python3
- yum install mpich
- yum install mpich-3.2
- yum install glog
- yum install lmdb
- yum install opencv
- yum install openblas
- yum install openblas-devel
- yum install zlib
- yum install python3-pillow
- yum install numactl numactl-libs numactl-devel
- yum install msgpack
- yum install libibverbs
- yum install libstdc++-devel
- yum install gcc gcc-c++

ubuntu18.04:
- apt install python3
- apt install python3-pip
- apt install python3-dev
- apt install libjpeg-dev zlib1g-dev
- apt install python3-pil
- apt install mpich
- apt install libgoogle-glog-dev 
- apt install liblmdb-dev
- apt install libopencv-dev
- apt install libopenblas-dev
- apt install libmsgpackc2
- apt install numactl
- apt install libnuma-dev
- apt install libmsgpack-dev
- apt install libstdc++-7-dev
- apt install gcc g++
- apt install pciutils

Python版本:
- Python 3.6

[Pytorch 安装步骤]
	- Pytorch 请使用目录中的whl 文件
	安装步骤：
	1 升级pip
        - python3 -m pip install pip --upgrade

	2 安装 torch
	pip3 install ./torch-1.10.0a0+git36449ea-cp36-cp36m-linux_x86_64.whl

	3 安装 torchvision
	pip3 install ./torchvision-0.11.0a0+fa347eb-cp36-cp36m-linux_x86_64.whl

	Example 验证：
	1,git clone https://github.com/pytorch/examples.git 
	2,cd examples/mnist 
	3,source /opt/rocm/set_env.sh
	4,python3 main.py --save-model


[TensorFlow 安装步骤]
    TF 使用本地whl 文件直接安装
	pip3 install ./tensorflow-1.15.8-cp36-cp36m-linux_x86_64.whl

	BenchMark 验证：
	1,git clone https://github.com/tensorflow/benchmarks.git -b cnn_tf_v2.1_compatible
	2,cd benchmarks/scripts/tf_cnn_benchmarks
	3,source /opt/rocm/set_env.sh
	4,python3 tf_cnn_benchmarks.py --num_gpus=1 --batch_size=16 --model=resnet50 --variable_update=parameter_server
	

[TensorFlow benchmark测试]
	1,进入tf-benchmarks-v1.15\scripts\tf_cnn_benchmarks目录
	2,chmod a+x test.sh test-step.sh
	3,进行benchmark测试
		1,单卡/单模型 测试用例如下
			python3 tf_cnn_benchmarks.py --num_gpus=1 --batch_size=64 --use_fp16=false --model=resnet50 --variable_update=parameter_server
			其中--num_gpus表示测试device数量,--model用于指定模型,--batch_size用于指定训练的batchsize,--use_fp16表示是否是float16模式(默认float32)
		
		2,多卡/单模型 测试用例如下
			python3 tf_cnn_benchmarks.py --num_gpus=4 --batch_size=64 --use_fp16=false --model=resnet50 --variable_update=parameter_server
			
		3,单卡/多模型 测试用例如下
			./test.sh -i 1 -b 32,64,128,256 -g 0 -n 1 -e false 
			其中-i表示总体测试几遍,-b表示测试哪些batchsize大小,-g表示在哪些device上面测试,-n表示用于测试的设备数量,-e表示是否使用float16模式
  
		4,多卡/多模型 测试用例如下
			./test.sh -i 1 -b 32,64,128,256 -g 0,1,2,3 -n 1,4 -e false #分别测试单卡和4卡模式
			./test.sh -i 1 -b 32,64,128,256 -g 0,1,2,3 -n 4 -e false #只测试4卡模式,4卡同时跑
			

[Pytorch benchmark测试]
	1,进入hy-pytorch-benchmarks-v1.0目录
	2,chmod a+x test.sh test-step.sh
	3,进行benchmark测试
		1,单卡/单模型 测试用例如下
			python3  benchmark-spawn.py -g 1 -d 0 -m resnet50 -i 200 -n 64
			其中-g表示测试device数量,-d表示在哪几个设备上测试,-m用于指定模型,-i表示循环多少次batchsize,-n表示batchsize大小,--fp16表示是否是float16模式(默认float32)
		
		2,多卡/单模型 测试用例如下
			python3  benchmark-spawn.py -g 4 -d 0,1,2,3 -m resnet50 -i 200 -n 64 
			
		3,单卡/多模型 测试用例如下
			./test.sh -i 1 -n 32,64,128,256 -d 0 -g 1 -e false
			其中-i表示总体测试几遍,-n表示测试哪些batchsize大小,-d表示在哪些device上面测试,-g表示用于测试的设备数量,-e表示是否使用float16模式
  
		4,多卡/多模型 测试用例如下
			./test.sh -i 1 -n 32,64,128,256 -d 0,1,2,3 -g 1,4 -e false #分别测试单卡和4卡模式
			./test.sh -i 1 -n 32,64,128,256 -d 0,1,2,3 -g 4 -e false #只测试4卡模式,4卡同时跑
```

```bash
pip3 install ./tensorflow-1.15.8-cp36-cp36m-linux_x86_64.whl
Processing ./tensorflow-1.15.8-cp36-cp36m-linux_x86_64.whl
Requirement already satisfied: six>=1.10.0 in /usr/local/lib/python3.6/site-packages (from tensorflow==1.15.8)
Requirement already satisfied: tensorflow-estimator==1.15.1 in /usr/local/lib/python3.6/site-packages (from tensorflow==1.15.8)
Requirement already satisfied: termcolor>=1.1.0 in /usr/local/lib/python3.6/site-packages (from tensorflow==1.15.8)
Requirement already satisfied: absl-py>=0.7.0 in /usr/local/lib/python3.6/site-packages (from tensorflow==1.15.8)
Requirement already satisfied: keras-preprocessing>=1.0.5 in /usr/local/lib64/python3.6/site-packages (from tensorflow==1.15.8)
Requirement already satisfied: astor>=0.6.0 in /usr/local/lib/python3.6/site-packages (from tensorflow==1.15.8)
Requirement already satisfied: grpcio>=1.8.6 in /usr/local/lib64/python3.6/site-packages (from tensorflow==1.15.8)
Requirement already satisfied: opt-einsum>=2.3.2 in /usr/local/lib/python3.6/site-packages (from tensorflow==1.15.8)
Requirement already satisfied: wheel>=0.26 in /usr/local/lib/python3.6/site-packages (from tensorflow==1.15.8)
Requirement already satisfied: numpy<2.0,>=1.16.0 in /usr/local/lib64/python3.6/site-packages (from tensorflow==1.15.8)
Requirement already satisfied: wrapt>=1.11.1 in /usr/local/lib64/python3.6/site-packages (from tensorflow==1.15.8)
Requirement already satisfied: tensorboard<1.16.0,>=1.15.0 in /usr/local/lib/python3.6/site-packages (from tensorflow==1.15.8)
Requirement already satisfied: protobuf>=3.6.1 in /usr/local/lib64/python3.6/site-packages (from tensorflow==1.15.8)
Requirement already satisfied: gast==0.2.2 in /usr/local/lib/python3.6/site-packages (from tensorflow==1.15.8)
Requirement already satisfied: google-pasta>=0.1.6 in /usr/local/lib/python3.6/site-packages (from tensorflow==1.15.8)
Requirement already satisfied: keras-applications>=1.0.8 in /usr/local/lib64/python3.6/site-packages (from tensorflow==1.15.8)
Requirement already satisfied: werkzeug>=0.11.15 in /usr/local/lib/python3.6/site-packages (from tensorboard<1.16.0,>=1.15.0->tensorflow==1.15.8)
Requirement already satisfied: setuptools>=41.0.0 in /usr/local/lib/python3.6/site-packages (from tensorboard<1.16.0,>=1.15.0->tensorflow==1.15.8)
Requirement already satisfied: markdown>=2.6.8 in /usr/local/lib64/python3.6/site-packages (from tensorboard<1.16.0,>=1.15.0->tensorflow==1.15.8)
Requirement already satisfied: h5py in /usr/local/lib64/python3.6/site-packages (from keras-applications>=1.0.8->tensorflow==1.15.8)
Requirement already satisfied: dataclasses; python_version < "3.7" in /usr/local/lib/python3.6/site-packages (from werkzeug>=0.11.15->tensorboard<1.16.0,>=1.15.0->tensorflow==1.15.8)
Requirement already satisfied: importlib-metadata>=4.4; python_version < "3.10" in /usr/local/lib/python3.6/site-packages (from markdown>=2.6.8->tensorboard<1.16.0,>=1.15.0->tensorflow==1.15.8)
Requirement already satisfied: typing-extensions>=3.6.4; python_version < "3.8" in /usr/local/lib/python3.6/site-packages (from importlib-metadata>=4.4; python_version < "3.10"->markdown>=2.6.8->tensorboard<1.16.0,>=1.15.0->tensorflow==1.15.8)
Requirement already satisfied: zipp>=0.5 in /usr/local/lib/python3.6/site-packages (from importlib-metadata>=4.4; python_version < "3.10"->markdown>=2.6.8->tensorboard<1.16.0,>=1.15.0->tensorflow==1.15.8)
Installing collected packages: tensorflow
Successfully installed tensorflow-1.15.8
```


# 5.2 yum 离线安装
libnet.x86_64
```bash
yumdownloader --resolve libnet.x86_64
yum localinstall libnet-1.1.6-7.el7.x86_64.rpm
```