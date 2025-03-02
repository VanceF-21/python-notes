<h1 id="Ldgcf">argparse</h1>
<h2 id="cqhQI">使用argparse模块</h2>
```python
# 引入argparser模块
import argparse

# 创建参数解析器
parser = argparse.ArgumentParser(description='这是一个命令行参数示例')
```

![](https://cdn.nlark.com/yuque/0/2024/png/46933974/1725350838707-9f68dd1e-2a30-4d95-94a2-98ceef47fde5.png)

```python
# 添加命令行参数
parser.add_argument('--arg1', type=str, help='参数1')
parser.add_argument('arg2', type=int, help='参数2')
```

![](https://cdn.nlark.com/yuque/0/2024/png/46933974/1725350907455-1335b75f-dc81-476a-95af-34ee6bc01933.png)

```python
# 解析命令行参数，获得一个args对象，包含所有参数的值
args = parser.parse_args()

# 获取参数值
arg1_value = args.arg1
arg2_value = args.arg2
```

<h2 id="Wsgdo">各类参数实例</h2>
<h3 id="MKUaa">位置参数</h3>
```python
# 位置参数 "xxx"
import argparse

# 1.创建参数解析器
parser = argparse.ArgumentParser(description='这是一个解析命令行参数示例')

# 2.添加位置参数（positional arguments）
parser.add_argument('arg1', type=int, help='位置参数1')
parser.add_argument('arg2', type=str, help='位置参数2')

# 3.解析命令行参数
args = parser.parse_args()

# 4.获取并打印参数值
print(args)
print(args.arg1)
print(args.arg2)
```

![](https://cdn.nlark.com/yuque/0/2024/png/46933974/1725351062378-e04a224b-7322-4c28-9ac4-d050db2d8896.png)

<h3 id="cK8EI">可选参数</h3>
```python
# 添加可选参数
import argparse

# 1.创建参数解析器
parser = argparse.ArgumentParser(description='这是一个解析命令行参数示例')

# 2.添加位置参数（positional arguments）
parser.add_argument('--option1', type=str, help='可选参数1')
parser.add_argument('--option2', type=str, help='可选参数2', default='a')
parser.add_argument('--option3', type=str, help='可选参数3', default='a')

# 3.解析命令行参数
args = parser.parse_args()

# 4.获取并打印参数值
print(args)
print(args.option1)
print(args.option2)
print(args.option3)
```

![](https://cdn.nlark.com/yuque/0/2024/png/46933974/1725351134752-02c9c4d3-3648-4f2e-980c-21dc6aab1df0.png)

<h3 id="YKXEZ">行为参数</h3>
```python
# 添加行为参数
# 行为参数只有两个值True和False
import argparse

# 1.创建参数解析器
parser = argparse.ArgumentParser(description='这是一个解析命令行参数示例')

# 2.添加行为参数（action arguments）
parser.add_argument('--action1', action='store_true', help='行为参数1')
parser.add_argument('--action2', action='store_true', help='行为参数2')

# 3.解析命令行参数
args = parser.parse_args()

# 4.获取并打印参数值
print(args)
print(args.action1)
print(args.action2)

```

![](https://cdn.nlark.com/yuque/0/2024/png/46933974/1725351174241-289a9800-028c-4991-9458-5895c8f1c91a.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46933974/1725351218840-57cffcc1-75e3-4686-825d-da614bc5b8c0.png)

<h3 id="I8xDX">短参数</h3>
```python
# 添加短参数
import argparse

# 1.创建参数解析器
parser = argparse.ArgumentParser(description='这是一个解析命令行参数示例')

# 2.添加短参数
parser.add_argument('-f', '--foo', type=str, help='短参数')

# 3.解析命令行参数
args = parser.parse_args()

# 4.获取并打印参数值
print(args)
print(args.foo)
```

![](https://cdn.nlark.com/yuque/0/2024/png/46933974/1725351279668-091d1ef8-ceee-402b-a02f-242a0601f847.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46933974/1725351294197-5cbc58df-7441-4d78-9978-8e2d00e13933.png)

<h2 id="NJuMM">查看帮助信息</h2>
![](https://cdn.nlark.com/yuque/0/2024/png/46933974/1725351330312-67d302e2-eea6-4716-9535-a280e03845c3.png)

```python
import argparse

# 1.创建参数解析器
parser = argparse.ArgumentParser(description='这是一个解析命令行参数示例')

# 2.添加位置参数（positional arguments）
parser.add_argument('arg1', type=int, help='位置参数1')
parser.add_argument('arg2', type=str, help='位置参数2')

# 2.添加可选参数（options arguments）
parser.add_argument('--option1', type=str, help='可选参数1')
parser.add_argument('--option2', type=str, help='可选参数2', default='a')
parser.add_argument('--option3', type=str, help='可选参数3', default='a')

# 2.添加行为参数（action arguments）
parser.add_argument('--action1', action='store_true', help='行为参数1')
parser.add_argument('--action2', action='store_true', help='行为参数2')

# 2.添加短参数
parser.add_argument('-f', '--foo', type=str, help='短参数')

# 3.解析命令行参数
args = parser.parse_args()

# 4.获取并打印参数值
print(args)
```

![](https://cdn.nlark.com/yuque/0/2024/png/46933974/1725351373251-f2825235-ca3c-4b81-8d18-6315d8011c04.png)

<h2 id="Fr19V">实战例子</h2>
```python
parser = argparse.ArgumentParser()
parser.add_argument('--dataset', default='cifar', help='The dataset of choice between "cifar" and "mnist".')
parser.add_argument('--batch_size', default=64, type=int, help='The batch size used for training.')
parser.add_argument('--epoch', default=20, type=int, help='Number of epochs for shadow and target model.')
parser.add_argument('--attack_epoch', default=50, type=int, help='Number of epochs for attack model.')
parser.add_argument('--only_eval', default=False, type=bool, help='If true, only evaluate trained loaded models.')
parser.add_argument('--save_new_models', default=False, type=bool, help='If true, trained models will be saved.')
args = parser.parse_args()
```

**解读：**

1. `**argparse.ArgumentParser()**`  
这一行创建了一个 `ArgumentParser` 对象，`ArgumentParser` 是 `argparse` 模块中的一个类，用来**处理命令行参数**。通过创建这个对象，程序可以定义它能够接受的参数以及每个参数的性质。
2. `**parser.add_argument('--dataset', default='cifar', help='The dataset of choice between "cifar" and "mnist".')**`  
这一行向 `ArgumentParser` 对象**添加了一个命令行参数** `--dataset`：
    - `--dataset` 是**参数的名称**，它是一个可选参数（以双破折号 `--` 开头）。
    - `default='cifar'` 指定了该**参数的默认值**为 `'cifar'`。
    - `help='The dataset of choice between "cifar" and "mnist".'` 是**帮助信息**，当用户请求帮助时会显示这条信息，解释这个参数的作用。该参数的作用是指定数据集的类型，可以选择 "cifar" 或 "mnist"。
3. `**parser.add_argument('--batch_size', default=64, type=int, help='The batch size used for training.')**`  
这一行向 `ArgumentParser` 对象**添加了一个命令行参数** `--batch_size`：
    - `default=64` 指定了默认的批量大小为 64。
    - `type=int` 指定了参数的类型为整数。
    - `help='The batch size used for training.'` 提供了帮助信息，解释这个参数是用于指定训练时使用的批量大小。
4. `**parser.add_argument('--epoch', default=20, type=int, help='Number of epochs for shadow and target model.')**`  
这一行添加了一个命令行参数 `--epoch`，用于指定影子模型和目标模型训练的轮数（epoch）：
    - `default=20` 指定默认值为 20。
    - `type=int` 指定参数类型为整数。
    - `help='Number of epochs for shadow and target model.'` 提供了帮助信息。
5. `**parser.add_argument('--attack_epoch', default=50, type=int, help='Number of epochs for attack model.')**`  
这一行添加了一个命令行参数 `--attack_epoch`，用于指定攻击模型训练的轮数：
    - `default=50` 指定默认值为 50。
    - `type=int` 指定参数类型为整数。
    - `help='Number of epochs for attack model.'` 提供了帮助信息。
6. `**parser.add_argument('--only_eval', default=False, type=bool, help='If true, only evaluate trained loaded models.')**`  
这一行添加了一个命令行参数 `--only_eval`，用于决定是否只评估训练好的模型：
    - `default=False` 指定默认值为 `False`。
    - `type=bool` 指定参数类型为布尔值。
    - `help='If true, only evaluate trained loaded models.'` 提供了帮助信息。
7. `**parser.add_argument('--save_new_models', default=False, type=bool, help='If true, trained models will be saved.')**`  
这一行添加了一个命令行参数 `--save_new_models`，用于决定是否保存新训练的模型：
    - `default=False` 指定默认值为 `False`。
    - `type=bool` 指定参数类型为布尔值。
    - `help='If true, trained models will be saved.'` 提供了帮助信息。
8. `**args = parser.parse_args()**`  
这一行代码调用了 `parse_args()` 方法，这个方法会**解析命令行输入的参数**，**并将结果存储在 **`**args**`** 对象中**。**通过 **`**args**`** 对象，可以访问每个参数的值，例如 **`**args.dataset**`**、**`**args.batch_size**`** 等**。

**知识点总结：**

+ `**argparse**`** 模块**：用于解析命令行参数，使得 Python 脚本可以从命令行获取用户输入。
+ **可选参数和位置参数**：`argparse` 支持定义两种参数类型：可选参数（带有 `--` 或 `-` 前缀）和位置参数（无前缀，必须提供）。
+ **默认值和类型**：通过 `default` 和 `type` 选项，可以为每个参数指定默认值和类型。
+ **帮助信息**：使用 `help` 提供参数的描述信息，帮助用户理解如何使用这些参数。

