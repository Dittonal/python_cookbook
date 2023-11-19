# 常见的神经网络
![](./imgs/mixtransformer.png)
# Torch

<h2 style="color: #ed7d31">Torch中的基本元素</h2>

``` python
import torch.nn as nn
```

### nn.Conv2d
- 常用参数 kernel_size,stride,padding,dilation
- 参数配置对通道数和尺寸的影响
### nn.BatchNorm2d


### nn.ReLU
### nn.Sequential
### grad
- 梯度就是对函数导数，梯度值就是函数在某一点的导数值，这里的某一点可以理解为图片的像素值
``` python
import torch
import torch.nn as nn
x = torch.tensor([[1.0, 2.0], [3.0, 4.0]], requires_grad=True)

# 定义一个函数，用于计算矩阵的某个元素的平方和
y = (x ** 2).sum()

# 计算梯度
y.backward()

# 打印梯度
print(x.grad)# tensor([[2., 4.],[6., 8.]])
```

> 对第一个点的计算方式为，y=x**2+4+9+16,在x=1处的导数是2;

> 第二个点，y=x**2+1+9+16,在x=2处导数为4;

<h3 style="color: #ed7d31">如果函数表达式改变</h3>

``` python
import torch
import torch.nn as nn
x = torch.tensor([[1.0, 2.0], [3.0, 4.0]], requires_grad=True)

# 定义一个函数 prod为乘积
y = (x ** 2).prod()

# 计算梯度
y.backward()

# 打印梯度
print(x.grad)# tensor([[1152.,  576.],[ 384.,  288.]])
```
> 计算方法，对第一个元素，`y=x**2*(4*9*16)`,求导结果是`(4*9*16)*2*x`,其余以此类推
