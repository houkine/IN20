# python基础

## 基本

+ 输入输出  
输出：print([string])  
输入: x=input([string])

+ 运算符  
加+，减-，乘*，除/  
取余%，** 幂运算(3**2意为3的2次方)  
大于>,小于<,等于==,不等于!=，小于等于<=,大于等于>=  
与&,或|,非!

+ 注释  
单行：#  
多行：''' 

+ 导入
import [文件名]

## 数据类型

+ 数字  
int,float,complex复数

+ 字符串  
str
len()长度,find()查找,replace()替换，slpit()切割

## 条件控制

+ 判断  
```
if true:
    print("true")
elif true:
    print("else if true")
else:
    print("false")
```

+ while  
```
while true:
    print("true")
else:
    print("false")
```

+ for  
```
# 打印数字从0到9
for i in range(0,10,1):
    print(i)
```
+ break  
强制跳出循环

+ continue  
结束当前循环

## 函数

+ def [函数名] (入参):   
```
def test(a,b):
    print(a+b)

test(1,2)
```

+ 调用  
函数名(入参)，如上

## 类
+ 定义  
class [类名]:

```
class Demo:
    i=123
    def print(self):
        print("class Demo,i="+str(self.i))

```

+ 成员方法：  
def [函数名] (self):  
self为必写入参，但不必传值，只是用于标记方法为类调用。

+ 调用  
先实例化，再使用变量名.属性/方法调用

```
x=Demo()
x.print()
```

+ 继承  
class [类名] (父类名):
```
class Demo:
    i=123
    def print(self):
        print("i="+str(self.i))

class Demo2(Demo):
    j=0

x=Demo2()
x.print()
```
结果为"i=123"  
python支持多继承，括号里写成(ClassA,ClassB)

+ 重写  
方法名和入参完全相同，则视为重写
```
class Demo:
    i=123
    def print(self):
        print("i="+str(self.i))

class Demo2(Demo):
    j=0
    def print(self):
        print("j="+str(self.j))

x=Demo2()
x.print()
```
结果为"j=0"

+ 私有private  
python定义为在变量名或者方法名前加上"__"则视为私有
例如上文中的变量i和方法print()  
```
__i=123
def __print(self):
```
外部就无法访问了

## 文件IO

+ 读  
```
f=open(file, mode='r')
```
方法为open，file为路径，相对或绝对，mode为读写权限，目前是可读

+ 写
```
f=open("E://test.txt", mode='w')
f.write("hello world")
f.close()
```
在E盘打开文件"test.txt"并写入。"w"会覆盖之前内容。如果文件不存在则创建。

+ 目录操作  
os对象

## 异常

+ 捕获  
使用try-except结构
```
try:
    x = int(input("请输入一个数字: "))
except ValueError:
    print("您输入的不是数字，请再次尝试输入！")
finally:
    print('这句话，无论异常是否发生都会执行。')
```

+ 抛出  
raise [Exception [, args [, traceback]]]

## 数据结构

+ 列表  
List=[x,x,...]  
类似于Arraylist，可变长度

+ 元组  
tup1 = ('Google', 'Runoob', 1997, 2000)
元祖值不可被修改

+ 字典  
d = {key1 : value1, key2 : value2 }  
类似于Map，以键值对存储数据

+ 集合  
parame = {value01,value02,...}
元素可以逐步添加，但是重复元素不会被添加进去。类似于Set