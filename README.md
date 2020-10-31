# DeepCube & DeepCubePlus
flask实现的一个完整的项目，用于在自己的服务器上部署DeepCubeA算法并可视化。
## 1. [DeepCube](http://czx.ac.cn/deepcube)
### 1.1 特别注意
1. 本项目要求在大内存下运行，本地运行需要2G内存
2. app.py为服务器运行文件，其中两个solve择一即可
    - 第一个solve函数为运行本地GPU计算
    - 第二个solve函数为调用原网页解法API
3. 在app.py中，增加这一行
    ```
    os.environ['CUDA_VISIBLE_DEVICES']='0'
    ```
   可以实现直接python app.py即可，作用是指定使用GPU 0
### 1.2 环境要求
1. Linux环境，非windows即可，本地mac、服务器CentOS、本地Ubuntu均测试成功
2. python == 2.7
3. tensorflow == 1.8.0
4. flask == 1.0
5. 其他包要求在requirments.txt

### 1.3 启动过程
```
pip install -r requirements.txt
cd flask
python app.py
```
### 1.4 目录结构安排
1. code
    - 存放深度学习求解魔方模型的代码
    - 详细解释参照code/README.md
    - 其中code\scripts\nnetSolve.py为魔方求解接口
2. flask
    - 存放flask服务器后端
    - 具体如下：
        - app.py：服务器运行文件
        - static：网页静态资源（js脚本等）
        - templates：存放页面html文件
3. environment
    - 原深度学习求解魔方模型的文件夹，暂无用
4. metadata
    - 原深度学习求解魔方模型的文件夹，暂无用
  
### 1.5 路由
1. "/"
    - GET接口，返回最早版本魔方求解页面
2. "/initState"
    - POST接口，魔方求解页面初始化状态用
3. "/solve"
    - POST接口，魔方求解页面求解用，发送魔方状态序列，返回求解步骤等
    
### 1.6 参考
1. Agostinelli, Forest, et al. "Solving the Rubik’s cube with deep reinforcement learning and search." Nature Machine Intelligence 1.8 (2019): 356-363.[[link]](https://www.nature.com/articles/s42256-019-0070-z.epdf?shared_access_token=-pCSsZa_J9bM8VyXLZLRctRgN0jAjWel9jnR3ZoTv0Osb8UCgUm5AQaSCMHWqWzsyV3KBcb13SAW-9IL1pAGd1HcSk40JSEjhoaBAi0ePvYh_5Dul6LvK0oJY1KI0ULo9O9HCut_y7aCTc93Th8m5g%3D%3D)
2. [DeepCubeA](https://codeocean.com/capsule/5723040/tree/v1) Source Code.

## 2. [DeepCubePlus](http://czx.ac.cn/deepcubeplus)
### 2.1 更新说明
在实现了DeepCube简单克隆之后，在Plus版中增加了以下前台功能：
1. 自由输入方式：旋转序列、涂色
2. 增加了单个旋转按钮
3. 增加了验证模块
4. 增加了魔方转动，展开图跟着变化

### 2.2 与普通版的不同文件
1. flask/static/main.plus.js文件，增加的前台功能都是在这个文件里的
2. flask/templates/index.plus.html文件，新版的主页
3. flask/app.plus.py文件，新版的运行文件，重写了solve方法

### 2.3 启动过程
```
pip install -r requirements.txt
cd flask
python app.plus.py
```

### 2.4 其他与普通版一致
