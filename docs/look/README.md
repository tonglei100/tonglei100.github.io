# Look

Look 是一款基于 CNN 训练的验证码识别工具，提供切图、训练、测试、识别等方法，优点是样本需求少，运行速度快，使用超级简单。


## 安装

### 前提条件

#### PyTorch 安装

访问 <https://pytorch.org/get-started/locally/>

找到适合自己的安装方式，如 Python3.6 的安装方式：

```shell
# Python 3.6
pip3 install http://download.pytorch.org/whl/cpu/torch-0.4.1-cp36-cp36m-win_amd64.whl
pip3 install torchvision
```

### look 安装

#### 初次安装

```shell
pip install look
```

#### 升级

```shell
pip install -U look
```

## 快速体验

在合适的目录，如 D:\\ 目录下，打开 CMD 命令行窗口，输入如下命令

```shell
look
cd look_example
python start.py
```

## 使用说明

### 1. 收集训练集图片，切图

收集验证码图片样本集，放在 **原始训练图集** 目录。

需要把验证码图片手工命名，格式：验证码\_时间戳，比如验证码图片上字符为 U6k4，则命名为 U6k4_1234567890.png。

如果验证码上字符有大小写，而实际输入不区分大小写，则可以全部命名为大写字母(建议做法)。

验证码的字符集需要和 setting.py 中定义的一致，请根据需要修改。

#### 切图

切图的前提条件是验证码字符能够等分切图，即：无黏连，并且都出现在固定位置，如：

![CUT](../_snapshot/captcha.png)

切图参数在 setting.py 的中 box 中配置。

如果验证码不符合切图条件，则跳过切图步骤，直接把验证码收集到 **训练图集** 目录。

#### 切图方法

切图方法如下，详细说明见示例代码说明

```python
cut_train()
```

### 2. 训练

训练方法如下，详细说明见示例代码说明

```python
train('model.pkl')
```

### 3. 收集测试集图片，切图

和 **1. 收集训练集图片，切图** 类似。(其实，也可以从训练图集剪切一部分到测试图集中)

### 4. 测试

和 **2. 训练** 类似。

```python
test('model.pkl')
```

### 5. 识别

识别方法如下，详细说明见示例代码说明

```python
code = recognize('model.pkl')
```
