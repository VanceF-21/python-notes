<h2 id="348fd3ee"><font style="color:rgb(79, 79, 79);">一、JSON是什么</font></h2>
JSON 是用于存储和交换数据的语法。JSON （JavaScript Object Notation）最初是用 JavaScript 对象表示法编写的文本，但随后成为了一种常见格式，被包括Python在内的众多语言采用。

<font style="color:rgb(77, 77, 77);">python里面的语言对象一般只有python能读懂，为了能比较好储存，而且能够让别的编程语言也能读懂这些数据，就会用json来转换储存。或者说把json数据类型的转化成python的数据类型</font>

<h3 id="ea54d42e"><font style="color:rgb(79, 79, 79);">1.json的数据类型和python数据类型的区别</font></h3>
![](https://cdn.nlark.com/yuque/0/2024/png/46933974/1725508241113-4bc1383d-2df4-409a-9789-80a7d1e63c3a.png)

<h3 id="bd8437dd"><font style="color:rgb(79, 79, 79);">2.json库的一些方法</font></h3>
![](https://cdn.nlark.com/yuque/0/2024/png/46933974/1725508285824-85f2e23a-bd67-44b7-87b5-965161b21536.png)

<h2 id="8f0f068c"><font style="color:rgb(79, 79, 79);">二、json.</font>[<font style="color:rgb(79, 79, 79);">dump</font>](https://so.csdn.net/so/search?q=dump&spm=1001.2101.3001.7020)<font style="color:rgb(79, 79, 79);">()和json.dumps()的区别</font></h2>
+ json.dumps()是把python对象转换成json对象的一个过程，生成的是**字符串**
+ json.dump()是把python对象转换成json对象生成一个**fp的文件流，和文件相关**

<h3 id="6b16e4d3"><font style="color:rgb(79, 79, 79);">1.json.dumps()</font></h3>
<font style="color:rgb(77, 77, 77);">在使用json方法的时候要记住先引进这个库，用import json</font>

```python
import json

x = {'name': '张三', 'age': 19, 'city': '南京'}

# 用dumps将python编码成json字符串
print(json.dumps(x))
# 输出：{"name": "\u4f60\u731c", "age": 19, "city": "\u56db\u5ddd"}
```

<font style="color:rgb(77, 77, 77);">这里就还有一个区别，注意我上面python字符串专门用的</font>**<font style="color:rgb(77, 77, 77);">单引号，转化以后，</font>****<font style="color:#DF2A3F;">json就用的是双引号了</font>**

<h3 id="87c78c50"><font style="color:rgb(79, 79, 79);">2.json.dump()</font></h3>
<font style="color:rgb(77, 77, 77);">这个方法结合了文件的操作，</font>**<font style="color:rgb(77, 77, 77);">把转换后的json储存在了文件里</font>**<font style="color:rgb(77, 77, 77);">（而不是直接输出json字符串）</font>

```python
import json

x = {'name': '张三', 'age': 19, 'city': '南京'}

# 将python编码成json放在那个文件里
filename = "pi_x.txt"
with open (filename, 'w') as f:
    json.dump(x, f)
```

然后，打开文件，就能看到编码后储存进去的json码：

![](https://cdn.nlark.com/yuque/0/2024/png/46933974/1725518020132-83d34523-a3ea-4768-b727-1ef5ea2277fd.png)

<h3 id="fc61ea41"><font style="color:rgb(79, 79, 79);">3.dumps的一些参数（重点）</font></h3>
<font style="color:rgb(77, 77, 77);">因为dumps编码以后的json格式输出比较的紧凑，如果不止一行看起来就不是特别好看，就像一堆乱码似的。所以，就推出了一些可选参数来让json码的可读性更高。当然，不用，就像我上面那样子也是OK滴。  
</font><font style="color:rgb(77, 77, 77);">参数如下：</font>

```python
json.dumps(obj, skipkeys=False, ensure_ascii=True, check_circular=True, allow_nan=True, cls=None, indent=None, separators=None, encoding="utf-8", default=None, sort_keys=False, **kw)
```

**<font style="color:#DF2A3F;">obj</font>**<font style="color:rgb(77, 77, 77);">:就是你要转化成json的对象。</font>  
**<font style="color:red;">sort_keys</font>**<font style="color:red;"> </font>**<font style="color:red;">= True</font>**<font style="color:red;">:是告诉编码器</font>**<font style="color:red;">按照字典排序(a到z)输出</font>**<font style="color:red;">。如果是字典类型的python对象，就把关键字按照字典排序</font>

```python
import json

x = {'name':'你猜','age':19,'city':'四川'}
y = json.dumps(x)
print(y)

z = json.dumps(x,sort_keys = True)
print(z)
```

输出：

```python
{"name": "\u4f60\u731c", "age": 19, "city": "\u56db\u5ddd"}
{"age": 19, "city": "\u56db\u5ddd", "name": "\u4f60\u731c"}
```

**<font style="color:rgb(255, 0, 0);">indent</font>**<font style="color:rgb(255, 0, 0);">:参数根据数据格式</font>**<font style="color:rgb(255, 0, 0);">缩进</font>**<font style="color:rgb(255, 0, 0);">显示，读起来更加清晰</font>

```python
import json

x = {'name':'你猜','age':19,'city':'四川'}

#用dumps将python编码成json字符串
y = json.dumps(x)
print(y)

z = json.dumps(x, indent=2)
print(z)
```

输出：

```python
{"name": "\u4f60\u731c", "age": 19, "city": "\u56db\u5ddd"}
{
  "name": "\u4f60\u731c",
  "age": 19,
  "city": "\u56db\u5ddd"
}
```

**<font style="color:rgb(255, 0, 0);">separators</font>**<font style="color:rgb(255, 0, 0);">:是分隔符的意思，参数意思分别为不同dict项之间的分隔符和dict项内key和value之间的分隔符，</font>**<font style="color:rgb(255, 0, 0);">把：和，后面的空格都除去了</font>**

```python
import json

x = {'name':'你猜','age':19,'city':'四川'}

#用dumps将python编码成json字符串
y = json.dumps(x)
print(y)

i = json.dumps(x,separators=(',',':'))
print(i)
```

输出：

```python
{"name": "\u4f60\u731c", "age": 19, "city": "\u56db\u5ddd"}
{"name":"\u4f60\u731c","age":19,"city":"\u56db\u5ddd"}
```

**<font style="color:rgb(255, 0, 0);">skipkeys</font>**<font style="color:rgb(255, 0, 0);">：默认值是False，如果dict的keys内的数据不是python的基本类型(str,unicode,int,long,float,bool,None)，设置为False时，就会报TypeError的错误。此时设置成True，则会跳过这类key </font>

```python
x = [ {'name':'你猜','age':19,'city':'四川',('hobby',):'Game'} ]

try:
    print(json.dumps(x))
except (TypeError, ValueError) as err:
    print ('ERROR:', err)
    
print()
json.dumps(x,skipkeys=True)
```

注意：**hobby那里使用的是元组[ ]**，输出是：

```python
ERROR: keys must be str, int, float, bool or None, not tuple

'[{"name": "\\u4f60\\u731c", "age": 19, "city": "\\u56db\\u5ddd"}]'
```

**<font style="color:rgb(255, 0, 0);">ensure_ascii=True</font>**<font style="color:rgb(255, 0, 0);">：默认输出ASCLL码，如果把这个该成False,就可以输出中文。</font>

```python
import json

x = {'name':'你猜','age':19,'city':'四川'}

#用dumps将python编码成json字符串
y = json.dumps(x)
print(y)

s = json.dumps(x,ensure_ascii=False)
print(s)
```

输出：

```python
{"name": "\u4f60\u731c", "age": 19, "city": "\u56db\u5ddd"}
{"name": "你猜", "age": 19, "city": "四川"}
```

**<font style="color:#DF2A3F;">check_circular</font>**<font style="color:#DF2A3F;">：如果check_circular为false，则跳过对容器类型的循环引用检查，循环引用将导致溢出错误(或更糟的情况)。</font>

**<font style="color:#DF2A3F;">allow_nan</font>**<font style="color:#DF2A3F;">：如果allow_nan为假，则ValueError将序列化超出范围的浮点值(nan、inf、-inf)，严格遵守JSON规范，而不是使用JavaScript等价值(nan、Infinity、-Infinity)。</font>

**<font style="color:#DF2A3F;">default</font>**<font style="color:#DF2A3F;">：default(obj)是一个函数，它应该返回一个可序列化的obj版本或引发类型错误。默认值只会引发类型错误。</font>

<h3 id="3da31d22"><font style="color:rgb(79, 79, 79);">4.dump的参数</font></h3>
```python
dump(obj, fp, skipkeys=False, ensure_ascii=True, check_circular=True,allow_nan=True, cls=None, indent=None, separators=None,default=None, sort_keys=False, **kw)
```

多了一个fp的文件参数

<h2 id="172eef4c"><font style="color:rgb(79, 79, 79);">三、json.load()和json.loads()的区别</font></h2>
+ json.loads()是针对内存对象，将string转换为dict
+ json.load()针对文件句柄，将json格式的字符转换为dict，从文件中读取 (将string转换为dict)

<h3 id="1babfc6c"><font style="color:rgb(79, 79, 79);">1.json.loads()</font></h3>
```python
import json

x = {'name':'你猜','age':19,'city':'四川'}

#用dumps将python编码成json字符串
x = json.dumps(x)
print(x)

#用loads将json编码成python
print(json.loads(x))
```

输出：

```python
{"name": "\u4f60\u731c", "age": 19, "city": "\u56db\u5ddd"}
{'name': '你猜', 'age': 19, 'city': '四川'}
```

<h3 id="ec3669b4"><font style="color:rgb(79, 79, 79);">2.json.load()</font></h3>
```python
import json

x = {'name':'你猜','age':19,'city':'四川'}

filename = 'pi_x.txt'
with open (filename,'w') as f:
    json.dump(x,f)
with open (filename) as f_1:
    print(json.load(f_1))
```

也是和文件有关，读取了pi_x.txt中的内容，输出：

```python
{'name': '你猜', 'age': 19, 'city': '四川'}
```

