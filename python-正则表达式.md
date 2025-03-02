<font style="color:rgb(51, 51, 51);">正则表达式是一个特殊的字符序列，它能帮助你方便的检查一个字符串是否与某种模式匹配。</font>

<font style="color:rgb(51, 51, 51);">在 Python 中，使用</font><font style="color:rgb(51, 51, 51);"> </font>**<font style="color:rgb(51, 51, 51);background-color:rgb(236, 234, 230);">re</font>**<font style="color:rgb(51, 51, 51);"> </font><font style="color:rgb(51, 51, 51);">模块来处理正则表达式。</font>

<font style="color:rgb(51, 51, 51);">re 模块提供了一组函数，允许你在字符串中进行</font>**<font style="color:rgb(51, 51, 51);">模式匹配、搜索和替换操作</font>**<font style="color:rgb(51, 51, 51);">。</font>

**<font style="color:rgb(51, 51, 51);background-color:rgb(236, 234, 230);">re</font>**<font style="color:rgb(51, 51, 51);"> 模块使 Python 语言拥有完整的正则表达式功能。</font>

<h2 id="e793fbe5"><font style="color:rgb(51, 51, 51);">re.match函数</font></h2>
<font style="color:rgb(51, 51, 51);">re.match 尝试</font>**<font style="color:rgb(51, 51, 51);">从字符串的起始位置匹配一个模式</font>**<font style="color:rgb(51, 51, 51);">，如果不是起始位置匹配成功的话，match() 就返回 None。</font>

**<font style="color:rgb(51, 51, 51);">函数语法</font>**<font style="color:rgb(51, 51, 51);">：</font>

```python
re.match(pattern, string, flags=0)
```

![](https://cdn.nlark.com/yuque/0/2024/png/46933974/1727062265670-ac27e77e-f65f-4a9f-813b-3d26db2e3b00.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46933974/1727062345508-e3835710-1af4-4b82-b55b-50a5faff3e1a.png)

```python
#!/usr/bin/python
 
import re
print(re.match('www', 'www.runoob.com').span())  # 在起始位置匹配
print(re.match('com', 'www.runoob.com'))         # 不在起始位置匹配
```

```python
(0, 3)
None
```

```python
#!/usr/bin/python3
import re
 
line = "Cats are smarter than dogs"
# .* 表示任意匹配除换行符（\n、\r）之外的任何单个或多个字符，并作为一个组保存（第一个捕获组）
# (.*?) 表示"非贪婪"模式，只保存第一个匹配到的子串，并作为一个组保存（第二个捕获组）
matchObj = re.match( r'(.*) are (.*?) .*', line, re.M|re.I)
# re.M|re.I：这是传递给 re.match() 的标志位。
# re.M 表示多行模式，而 re.I 表示忽略大小写

if matchObj:
   print ("matchObj.group() : ", matchObj.group())  # 打印整个匹配的结果
   print ("matchObj.group(1) : ", matchObj.group(1))  # 打印第一个捕获组的结果
   print ("matchObj.group(2) : ", matchObj.group(2))  # 打印第二个捕获组的结果
else:
   print ("No match!!")
```

```python
matchObj.group() :  Cats are smarter than dogs
matchObj.group(1) :  Cats
matchObj.group(2) :  smarter
```

<h2 id="cdd0244d"><font style="color:rgb(51, 51, 51);">re.search方法</font></h2>
<font style="color:rgb(51, 51, 51);">re.search </font>**<font style="color:rgb(51, 51, 51);">扫描整个字符串并返回</font>****<font style="color:#DF2A3F;">第一个</font>****<font style="color:rgb(51, 51, 51);">成功的匹配</font>**<font style="color:rgb(51, 51, 51);">。</font>

<font style="color:rgb(51, 51, 51);">函数语法：</font>

```python
re.search(pattern, string, flags=0)
```

![](https://cdn.nlark.com/yuque/0/2024/png/46933974/1727062558239-bd7284e1-c496-40b0-a3b5-ac407013fad5.png)

```python
#!/usr/bin/python3
 
import re
 
print(re.search('www', 'www.runoob.com').span())  # 在起始位置匹配
print(re.search('com', 'www.runoob.com').span())  # 不在起始位置匹配
```

```python
(0, 3)
(11, 14)
```

```python
#!/usr/bin/python3
 
import re
 
line = "Cats are smarter than dogs"
 
searchObj = re.search( r'(.*) are (.*?) .*', line, re.M|re.I)
 
if searchObj:
   print ("searchObj.group() : ", searchObj.group())
   print ("searchObj.group(1) : ", searchObj.group(1))
   print ("searchObj.group(2) : ", searchObj.group(2))
else:
   print ("Nothing found!!")
```

```python
searchObj.group() :  Cats are smarter than dogs
searchObj.group(1) :  Cats
searchObj.group(2) :  smarter
```

<h2 id="442cdd73"><font style="color:rgb(51, 51, 51);">re.match 与 re.search的区别</font></h2>
+ **<font style="color:rgb(51, 51, 51);background-color:rgb(236, 234, 230);">re.match</font>**<font style="color:rgb(51, 51, 51);"> </font>**<font style="color:rgb(51, 51, 51);">只匹配字符串的开始（从头开始）</font>**<font style="color:rgb(51, 51, 51);">，如果字符串开始不符合正则表达式，则匹配失败，函数返回 None</font>
+ <font style="color:rgb(51, 51, 51);"></font>**<font style="color:rgb(51, 51, 51);background-color:rgb(236, 234, 230);">re.search</font>**<font style="color:rgb(51, 51, 51);"> </font>**<font style="color:rgb(51, 51, 51);">匹配整个字符串（存在即可）</font>**<font style="color:rgb(51, 51, 51);">，直到找到一个匹配。</font>

```python
#!/usr/bin/python3
 
import re
 
line = "Cats are smarter than dogs"
 
matchObj = re.match( r'dogs', line, re.M|re.I)
if matchObj:
   print ("match --> matchObj.group() : ", matchObj.group())
else:
   print ("No match!!")
 
matchObj = re.search( r'dogs', line, re.M|re.I)
if matchObj:
   print ("search --> matchObj.group() : ", matchObj.group())
else:
   print ("No match!!")
```

```python
No match!!
search --> matchObj.group() :  dogs
```

<h2 id="459076c9"><font style="color:rgb(51, 51, 51);">检索和替换</font></h2>
<font style="color:rgb(51, 51, 51);">Python 的re模块提供了</font>**<font style="color:rgb(51, 51, 51);">re.sub用于替换字符串中的匹配项</font>**<font style="color:rgb(51, 51, 51);">。</font>

<font style="color:rgb(51, 51, 51);">语法：</font>

```python
re.sub(pattern, repl, string, count=0, flags=0)
```

![](https://cdn.nlark.com/yuque/0/2024/png/46933974/1727074904179-7a7b36d8-32f7-402d-91f2-530e35331863.png)

```python
#!/usr/bin/python3
import re
 
phone = "2004-959-559 # 这是一个电话号码"
 
# 删除注释
num = re.sub(r'#.*$', "", phone)
print ("电话号码 : ", num)
 
# 移除非数字的内容
num = re.sub(r'\D', "", phone)
print ("电话号码 : ", num)
```

```python
电话号码 :  2004-959-559 
电话号码 :  2004959559
```

<h3 id="5ad8e8e3"><font style="color:rgb(51, 51, 51);">repl 参数是一个函数</font></h3>
<font style="color:rgb(51, 51, 51);">以下实例中将字符串中的匹配的数字乘以 2：</font>

```python
#!/usr/bin/python
 
import re
 
# 将匹配的数字乘以 2
def double(matched):
    """
        接收一个正则表达式的匹配对象matched，从中提取出捕获的数字部分，
        将其转换成整数，然后将该数字乘以2，返回字符串形式
    """
    value = int(matched.group('value'))
    return str(value * 2)
 
s = 'A23G4HFD567'
print(re.sub('(?P<value>\d+)', double, s))
# 替换操作：(?P<value> ... ) 是一个命名捕获组，它允许我们通过名称 value 来引用匹配的部分。
# \d+ 匹配一个或多个数字
# double是替换函数
```

```python
A46G8HFD1134  # 23变成46，567变成1134
```

<h3 id="e6a73f2e"><font style="color:rgb(51, 51, 51);">compile 函数</font></h3>
<font style="color:rgb(51, 51, 51);">compile 函数用于</font>**<font style="color:rgb(51, 51, 51);">编译正则表达式</font>**<font style="color:rgb(51, 51, 51);">，</font>**<font style="color:rgb(51, 51, 51);">生成一个正则表达式（ Pattern ）对象，供 match() 和 search() 这两个函数使用</font>**<font style="color:rgb(51, 51, 51);">。</font>

<font style="color:rgb(51, 51, 51);">语法格式为：</font>

```python
re.compile(pattern[, flags])
```

![](https://cdn.nlark.com/yuque/0/2024/png/46933974/1727075402306-98718bb3-abda-47dc-8a31-2f8b89748e8d.png)

```python
>>>import re
>>> pattern = re.compile(r'\d+')                    # 用于匹配至少一个数字
>>> m = pattern.match('one12twothree34four')        # 查找头部，没有匹配
>>> print( m )
None
>>> m = pattern.match('one12twothree34four', 2, 10) # 从'e'的位置开始匹配，没有匹配
>>> print( m )
None
>>> m = pattern.match('one12twothree34four', 3, 10) # 从'1'的位置开始匹配，正好匹配
>>> print( m )                                        # 返回一个 Match 对象
<_sre.SRE_Match object at 0x10a42aac0>
>>> m.group(0)   # 可省略 0
'12'
>>> m.start(0)   # 可省略 0
3
>>> m.end(0)     # 可省略 0
5
>>> m.span(0)    # 可省略 0
(3, 5)
```

![](https://cdn.nlark.com/yuque/0/2024/png/46933974/1727075488093-1e3d8402-6de8-4937-88b6-9c0e08571450.png)

```python
>>>import re
>>> pattern = re.compile(r'([a-z]+) ([a-z]+)', re.I)   # re.I 表示忽略大小写
>>> m = pattern.match('Hello World Wide Web')
>>> print( m )                            # 匹配成功，返回一个 Match 对象
<_sre.SRE_Match object at 0x10bea83e8>
>>> m.group(0)                            # 返回匹配成功的整个子串
'Hello World'
>>> m.span(0)                             # 返回匹配成功的整个子串的索引
(0, 11)
>>> m.group(1)                            # 返回第一个分组匹配成功的子串
'Hello'
>>> m.span(1)                             # 返回第一个分组匹配成功的子串的索引
(0, 5)
>>> m.group(2)                            # 返回第二个分组匹配成功的子串
'World'
>>> m.span(2)                             # 返回第二个分组匹配成功的子串索引
(6, 11)
>>> m.groups()                            # 等价于 (m.group(1), m.group(2), ...)
('Hello', 'World')
>>> m.group(3)                            # 不存在第三个分组
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: no such group
```

<h3 id="findall"><font style="color:rgb(51, 51, 51);">findall</font></h3>
**<font style="color:rgb(51, 51, 51);">在字符串中找到正则表达式所匹配的所有子串，并返回一个列表</font>**<font style="color:rgb(51, 51, 51);">，如果有多个匹配模式，则返回</font>**<font style="color:rgb(51, 51, 51);">元组列表</font>**<font style="color:rgb(51, 51, 51);">，如果没有找到匹配的，则返回</font>**<font style="color:rgb(51, 51, 51);">空列表</font>**<font style="color:rgb(51, 51, 51);">。</font>

**<font style="color:rgb(51, 51, 51);">注意：</font>****<font style="color:#DF2A3F;"> match 和 search 是匹配一次 ，findall 匹配所有</font>**<font style="color:rgb(51, 51, 51);">。</font>

<font style="color:rgb(51, 51, 51);">语法格式为：</font>

```python
re.findall(pattern, string, flags=0)
或
pattern.findall(string[, pos[, endpos]])
```

![](https://cdn.nlark.com/yuque/0/2024/png/46933974/1727075966012-bd744c2f-17c5-4e14-8a20-11d72181bf95.png)

<font style="color:rgb(51, 51, 51);">查找字符串中的所有数字：</font>

```python
import re
 
result1 = re.findall(r'\d+','runoob 123 google 456')
 
pattern = re.compile(r'\d+')   # 查找数字
result2 = pattern.findall('runoob 123 google 456')
result3 = pattern.findall('run88oob123google456', 0, 10)
 
print(result1)
print(result2)
print(result3)
```

```python
['123', '456']
['123', '456']
['88', '12']
```

<font style="color:rgb(51, 51, 51);">多个匹配模式，返回元组列表：</font>

```python
import re

result = re.findall(r'(\w+)=(\d+)', 'set width=20 and height=10')
print(result)
```

```python
[('width', '20'), ('height', '10')]
```

<h3 id="re.finditer"><font style="color:rgb(51, 51, 51);">re.finditer</font></h3>
<font style="color:rgb(51, 51, 51);">和 findall 类似，</font>**<font style="color:rgb(51, 51, 51);">在字符串中找到正则表达式所匹配的所有子串，并把它们作为一个迭代器返回</font>**<font style="color:rgb(51, 51, 51);">。</font>

```python
re.finditer(pattern, string, flags=0)
```

![](https://cdn.nlark.com/yuque/0/2024/png/46933974/1727076115389-2c505c9e-a8fe-4866-af73-c45c88257200.png)

```python
import re
 
it = re.finditer(r"\d+","12a32bc43jf3") 
for match in it: 
    print (match.group() )
```

```python
12 
32 
43 
3
```

<h3 id="re.split"><font style="color:rgb(51, 51, 51);">re.split</font></h3>
<font style="color:rgb(51, 51, 51);">split 方法按照</font>**<font style="color:rgb(51, 51, 51);">能够匹配的子串将字符串分割后返回列表</font>**<font style="color:rgb(51, 51, 51);">，它的使用形式如下：</font>

```python
re.split(pattern, string[, maxsplit=0, flags=0])
```

![](https://cdn.nlark.com/yuque/0/2024/png/46933974/1727076174295-338991e2-22d9-4db1-87bb-aa63e166e073.png)

```python
>>>import re
>>> re.split('\W+', 'runoob, runoob, runoob.')
['runoob', 'runoob', 'runoob', '']
>>> re.split('(\W+)', ' runoob, runoob, runoob.') 
['', ' ', 'runoob', ', ', 'runoob', ', ', 'runoob', '.', '']
>>> re.split('\W+', ' runoob, runoob, runoob.', 1) 
['', 'runoob, runoob, runoob.']
 
>>> re.split('a*', 'hello world')   # 对于一个找不到匹配的字符串而言，split 不会对其作出分割
['hello world']
```

<h2 id="9622e461"><font style="color:rgb(51, 51, 51);">正则表达式对象</font></h2>
<h3 id="re.regexobject"><font style="color:rgb(51, 51, 51);">re.RegexObject</font></h3>
<font style="color:rgb(51, 51, 51);">re.compile() 返回 RegexObject 对象。</font>

<h3 id="re.matchobject"><font style="color:rgb(51, 51, 51);">re.MatchObject</font></h3>
<font style="color:rgb(51, 51, 51);">group() 返回被 RE 匹配的字符串。</font>

+ **<font style="color:rgb(51, 51, 51);background-color:rgb(236, 234, 230);">start()</font>**<font style="color:rgb(51, 51, 51);"> </font><font style="color:rgb(51, 51, 51);">返回匹配开始的位置</font>
+ **<font style="color:rgb(51, 51, 51);background-color:rgb(236, 234, 230);">end()</font>**<font style="color:rgb(51, 51, 51);"> </font><font style="color:rgb(51, 51, 51);">返回匹配结束的位置</font>
+ **<font style="color:rgb(51, 51, 51);background-color:rgb(236, 234, 230);">span()</font>**<font style="color:rgb(51, 51, 51);"> 返回一个元组包含匹配 (开始,结束) 的位置</font>

<h2 id="flags"><font style="color:rgb(51, 51, 51);">正则表达式修饰符 - 可选标志</font></h2>
<font style="color:rgb(51, 51, 51);">正则表达式可以包含一些可选标志修饰符来控制匹配的模式。</font>

<font style="color:rgb(51, 51, 51);">以下标志可以单独使用，也可以通过按位或（|）组合使用。例如，re.IGNORECASE | re.MULTILINE 表示同时启用忽略大小写和多行模式。</font>

![](https://cdn.nlark.com/yuque/0/2024/png/46933974/1727076344249-16984af9-70ec-431c-82ee-99b44cc02abe.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46933974/1727076358830-79de144d-1479-40a7-ad71-5027a3d97237.png)

<h2 id="vFoZO"><font style="color:rgb(51, 51, 51);">正则表达式模式</font></h2>
<font style="color:rgb(51, 51, 51);">模式字符串使用特殊的语法来表示一个正则表达式。</font>

**<font style="color:rgb(51, 51, 51);">字母和数字表示他们自身</font>**<font style="color:rgb(51, 51, 51);">。一个正则表达式模式中的字母和数字匹配同样的字符串。</font>

<font style="color:rgb(51, 51, 51);">多数字母和数字前加一个反斜杠时会拥有不同的含义。</font>

<font style="color:rgb(51, 51, 51);">标点符号只有被转义时才匹配自身，否则它们表示特殊的含义。</font>

<font style="color:rgb(51, 51, 51);">反斜杠本身需要使用反斜杠转义。</font>

<font style="color:rgb(51, 51, 51);">由于正则表达式通常都包含反斜杠，所以你最好使用原始字符串来表示它们。模式元素(如</font><font style="color:rgb(51, 51, 51);"> </font>**<font style="color:rgb(51, 51, 51);background-color:rgb(236, 234, 230);">r'\t'</font>**<font style="color:rgb(51, 51, 51);">，等价于</font><font style="color:rgb(51, 51, 51);"> </font>**<font style="color:rgb(51, 51, 51);background-color:rgb(236, 234, 230);">\\t</font>**<font style="color:rgb(51, 51, 51);"> </font><font style="color:rgb(51, 51, 51);">)匹配相应的特殊字符。</font>

<font style="color:rgb(51, 51, 51);">下表列出了正则表达式模式语法中的特殊元素。如果你使用模式的同时提供了可选的标志参数，某些模式元素的含义会改变。</font>

| <font style="color:rgb(255, 255, 255);">模式</font> | <font style="color:rgb(255, 255, 255);">描述</font> |
| --- | --- |
| <font style="color:rgb(51, 51, 51);">^</font> | <font style="color:rgb(51, 51, 51);">匹配字符串的</font>**<font style="color:rgb(51, 51, 51);">开头</font>** |
| <font style="color:rgb(51, 51, 51);">$</font> | <font style="color:rgb(51, 51, 51);">匹配字符串的</font>**<font style="color:rgb(51, 51, 51);">末尾</font>**<font style="color:rgb(51, 51, 51);">。</font> |
| <font style="color:rgb(51, 51, 51);">.</font> | **<font style="color:rgb(51, 51, 51);">匹配任意字符，除了换行符</font>**<font style="color:rgb(51, 51, 51);">，当re.DOTALL标记被指定时，则可以匹配包括换行符的任意字符。</font> |
| <font style="color:rgb(51, 51, 51);">[...]</font> | <font style="color:rgb(51, 51, 51);">用来匹配所包含的</font>**<font style="color:#DF2A3F;">任意一个字符</font>**<font style="color:rgb(51, 51, 51);">，例如 [amk] 匹配 'a'，'m'或'k'</font> |
| <font style="color:rgb(51, 51, 51);">[^...]</font> | **<font style="color:#DF2A3F;">不在[]中的字符</font>**<font style="color:rgb(51, 51, 51);">：[^abc] 匹配除了a,b,c之外的字符。</font> |
| <font style="color:rgb(51, 51, 51);">re*</font> | <font style="color:rgb(51, 51, 51);">匹配</font>**<font style="color:rgb(51, 51, 51);">0个或多个</font>**<font style="color:rgb(51, 51, 51);">的表达式。</font> |
| <font style="color:rgb(51, 51, 51);">re+</font> | <font style="color:rgb(51, 51, 51);">匹配</font>**<font style="color:rgb(51, 51, 51);">1个或多个</font>**<font style="color:rgb(51, 51, 51);">的表达式。</font> |
| <font style="color:rgb(51, 51, 51);">re?</font> | <font style="color:rgb(51, 51, 51);">匹配</font>**<font style="color:rgb(51, 51, 51);">0个或1个</font>**<font style="color:rgb(51, 51, 51);">由前面的正则表达式定义的片段，非贪婪方式</font> |
| <font style="color:rgb(51, 51, 51);">re{ n}</font> | <font style="color:rgb(51, 51, 51);">匹配</font>**<font style="color:rgb(51, 51, 51);">n个前面表达式</font>**<font style="color:rgb(51, 51, 51);">。例如，"o{2}"不能匹配"Bob"中的"o"，但是能匹配"food"中的两个o。</font> |
| <font style="color:rgb(51, 51, 51);">re{ n,}</font> | **<font style="color:rgb(51, 51, 51);">精确匹配n个前面表达式</font>**<font style="color:rgb(51, 51, 51);">。例如，"o{2,}"不能匹配"Bob"中的"o"，但能匹配"foooood"中的所有o。"o{1,}"等价于"o+"。"o{0,}"则等价于"o*"。</font> |
| <font style="color:rgb(51, 51, 51);">re{ n, m}</font> | <font style="color:rgb(51, 51, 51);">匹配 </font>**<font style="color:rgb(51, 51, 51);">n 到 m 次由前面的正则表达式定义的片段</font>**<font style="color:rgb(51, 51, 51);">，贪婪方式</font> |
| <font style="color:rgb(51, 51, 51);">a| b</font> | <font style="color:rgb(51, 51, 51);">匹配</font>**<font style="color:rgb(51, 51, 51);">a或b</font>** |
| <font style="color:rgb(51, 51, 51);">(re)</font> | **<font style="color:rgb(51, 51, 51);">匹配括号内的表达式</font>**<font style="color:rgb(51, 51, 51);">，也表示</font>**<font style="color:#DF2A3F;">一个组</font>** |
| <font style="color:rgb(51, 51, 51);">(?imx)</font> | <font style="color:rgb(51, 51, 51);">正则表达式包含三种可选标志：i, m, 或 x 。只影响括号中的区域。</font> |
| <font style="color:rgb(51, 51, 51);">(?-imx)</font> | <font style="color:rgb(51, 51, 51);">正则表达式关闭 i, m, 或 x 可选标志。只影响括号中的区域。</font> |
| <font style="color:rgb(51, 51, 51);">(?: re)</font> | <font style="color:rgb(51, 51, 51);">类似 (...), 但是不表示一个组</font> |
| <font style="color:rgb(51, 51, 51);">(?imx: re)</font> | <font style="color:rgb(51, 51, 51);">在括号中使用i, m, 或 x 可选标志</font> |
| <font style="color:rgb(51, 51, 51);">(?-imx: re)</font> | <font style="color:rgb(51, 51, 51);">在括号中不使用i, m, 或 x 可选标志</font> |
| <font style="color:rgb(51, 51, 51);">(?#...)</font> | <font style="color:rgb(51, 51, 51);">注释.</font> |
| <font style="color:rgb(51, 51, 51);">(?= re)</font> | <font style="color:rgb(51, 51, 51);">前向肯定界定符。如果所含正则表达式，以 ... 表示，在当前位置成功匹配时成功，否则失败。但一旦所含表达式已经尝试，匹配引擎根本没有提高；模式的剩余部分还要尝试界定符的右边。</font> |
| <font style="color:rgb(51, 51, 51);">(?! re)</font> | <font style="color:rgb(51, 51, 51);">前向否定界定符。与肯定界定符相反；当所含表达式不能在字符串当前位置匹配时成功。</font> |
| <font style="color:rgb(51, 51, 51);">(?> re)</font> | <font style="color:rgb(51, 51, 51);">匹配的独立模式，省去回溯。</font> |
| <font style="color:rgb(51, 51, 51);">\w</font> | <font style="color:rgb(51, 51, 51);">匹配</font>**<font style="color:rgb(51, 51, 51);">数字字母下划线</font>** |
| <font style="color:rgb(51, 51, 51);">\W</font> | <font style="color:rgb(51, 51, 51);">匹配</font>**<font style="color:rgb(51, 51, 51);">非数字字母下划线</font>** |
| <font style="color:rgb(51, 51, 51);">\s</font> | <font style="color:rgb(51, 51, 51);">匹配</font>**<font style="color:rgb(51, 51, 51);">任意空白字符</font>**<font style="color:rgb(51, 51, 51);">，等价于 [\t\n\r\f]。</font> |
| <font style="color:rgb(51, 51, 51);">\S</font> | <font style="color:rgb(51, 51, 51);">匹配</font>**<font style="color:rgb(51, 51, 51);">任意非空字符</font>** |
| <font style="color:rgb(51, 51, 51);">\d</font> | <font style="color:rgb(51, 51, 51);">匹配</font>**<font style="color:rgb(51, 51, 51);">任意数字</font>**<font style="color:rgb(51, 51, 51);">，等价于 </font>**<font style="color:rgb(51, 51, 51);">[0-9]</font>**<font style="color:rgb(51, 51, 51);">。</font> |
| <font style="color:rgb(51, 51, 51);">\D</font> | <font style="color:rgb(51, 51, 51);">匹配</font>**<font style="color:rgb(51, 51, 51);">任意非数字</font>** |
| <font style="color:rgb(51, 51, 51);">\A</font> | <font style="color:rgb(51, 51, 51);">匹配</font>**<font style="color:rgb(51, 51, 51);">字符串开始</font>** |
| <font style="color:rgb(51, 51, 51);">\Z</font> | <font style="color:rgb(51, 51, 51);">匹配</font>**<font style="color:rgb(51, 51, 51);">字符串结束</font>**<font style="color:rgb(51, 51, 51);">，如果是存在换行，只匹配到换行前的结束字符串。</font> |
| <font style="color:rgb(51, 51, 51);">\z</font> | <font style="color:rgb(51, 51, 51);">匹配字符串结束</font> |
| <font style="color:rgb(51, 51, 51);">\G</font> | <font style="color:rgb(51, 51, 51);">匹配</font>**<font style="color:rgb(51, 51, 51);">最后匹配完成的位置</font>**<font style="color:rgb(51, 51, 51);">。</font> |
| <font style="color:rgb(51, 51, 51);">\b</font> | <font style="color:rgb(51, 51, 51);">匹配</font>**<font style="color:rgb(51, 51, 51);">一个单词边界</font>**<font style="color:rgb(51, 51, 51);">，也就是指</font>**<font style="color:rgb(51, 51, 51);">单词和空格间的位置</font>**<font style="color:rgb(51, 51, 51);">。例如， 'er\b' 可以匹配"never" 中的 'er'，但不能匹配 "verb" 中的 'er'。</font> |
| <font style="color:rgb(51, 51, 51);">\B</font> | <font style="color:rgb(51, 51, 51);">匹配</font>**<font style="color:rgb(51, 51, 51);">非单词边界</font>**<font style="color:rgb(51, 51, 51);">。'er\B' 能匹配 "verb" 中的 'er'，但不能匹配 "never" 中的 'er'。</font> |
| <font style="color:rgb(51, 51, 51);">\n, \t, 等。</font> | **<font style="color:rgb(51, 51, 51);">匹配一个换行符</font>**<font style="color:rgb(51, 51, 51);">。匹配一个制表符, 等</font> |
| <font style="color:rgb(51, 51, 51);">\1...\9</font> | <font style="color:rgb(51, 51, 51);">匹配</font>**<font style="color:rgb(51, 51, 51);">第n个分组的内容</font>**<font style="color:rgb(51, 51, 51);">。</font> |
| <font style="color:rgb(51, 51, 51);">\10</font> | <font style="color:rgb(51, 51, 51);">匹配</font>**<font style="color:rgb(51, 51, 51);">第n个分组的内容</font>**<font style="color:rgb(51, 51, 51);">，如果它经匹配。否则指的是八进制字符码的表达式。</font> |


