# mofang_proj
使用flask框架所实现的魔方项目，在本地服务器部署运行
## 1. 项目说明（github地址：https://github.com/Deacychen257/mofang/tree/master，master分支）
### 1.1 环境要求
1. Linux环境（Ubuntu16.04测试成功）
2. python == 2.7
3. tensorflow == 1.8.0
4. flask == 1.0
5. virtualenv（python2版本）
6. 更多模块要求在requirments.txt可见

### 1.2 启动过程（上述环境安装好后）
-----------------------------------------------------------------------------------------------------------------------------------------------------------------
1.  安装完虚拟环境后，使用命令“mkvirtualenv 环境名”创建虚拟环境,并使用命令“workon 环境名”进入虚拟环境
2.  在虚拟环境下，使用“pip install -r requirements.txt”命令安装项目的依赖包
3.  cd到项目文件夹下的mofang文件夹中
4.  使用命令“python start.py”在本地部署项目并开启服务
5.  flask默认打开端口5000，所以在浏览器中输入127.0.0.1:5000，即可访问魔方页面
-----------------------------------------------------------------------------------------------------------------------------------------------------------------

### 1.3 目录结构安排
1. code
    - 存放深度学习求解魔方模型的算法代码
    - code\scripts\nnetSolve.py为魔方求解接口
    - code\savedModels为已训练好的模型
2. mofang
    - 存放有使用flask框架开发的前后端文件
    - 文件作用介绍：
        - start.py：开启服务器文件，包括路由与路由对应调取的执行函数
	        -"/":该路由的功能为调取魔方html页面返回给客户端请求
	        -"/initState":该路由的功能为调取初始化initState函数，完成初始化josn数据给ajax请求，完成初始化
	        -"/solve":该路由的功能为调取sovle函数，完成对魔方的求解
        - "tools.py":在调取solve函数时，在solve函数中再调取tools.py中求解魔方并返回数据的函数
        - static：存放网页静态js、css等资源
        - templates：存放魔方页面html文件
3. data
    - 保存用于训练魔方所需的数据集

### 1.4 注意事项
*  在tools.py中指定了os.environ['CUDA_VISIBLE_DEVICES']='0'，即使用了0个GPU
*  本项目没有拉取docker作为镜像，使用时可以自己制作镜像并根据requirements.txt安装环境，也可以拉取参考项目中的源镜像作为父镜像

### 1.5 参考
1. deepcube论文：Agostinelli, Forest, et al. "Solving the Rubik’s cube with deep reinforcement learning and search." Nature Machine Intelligence 1.8 (2019): 356-363.
2. 后端参考：https://codeocean.com/capsule/5723040/tree/v1. && https://github.com/yeates/deepcube-full
3. 前端参考：http://deepcube.igb.uci.edu
