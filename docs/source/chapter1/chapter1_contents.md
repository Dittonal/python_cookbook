# sphinx简单使用
- 本项目在python3.9下安装sphinx
- 大部分代码来自[模板](https://github.com/readthedocs/tutorial-template)
- clash 开启后github依旧无法提交代码的解决方案
  - 开启允许本地局域网

``` bash
git config --global https.proxy http://127.0.0.1:7890
git config --global http.proxy http://127.0.0.1:7890
``` 
- 本地调试命令

``` bash
sphinx-autobuild source build/html
``` 
# MarkDown示例用法

## 二级标题

### 三级标题

#### 四级标题

*斜体测试*

**加粗测试**

<u>下划线测试</u>

~~删除线~~ <s>删除线（开启识别HTML标签时）</s>



**粗体**  __粗体__

***粗斜体*** ___粗斜体___

上标：X<sub>2</sub>，下标：O<sup>2</sup>

==高亮测试==


$expression$

`int`


<!--注释测试-->


<h5> [超链接测试](www.baidu.com) </h5>


 | 作者 | 朝代 | 评分 |
 | :--: | :--: | :--: |
 | 李白 |  唐  | 100  |


```shell
echo $PATH
```


$$
expression
$$

1. 有序列表

2. 有序列表


- 无序列表


- [ ] 任务列表



------



>引用测试



