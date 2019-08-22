**文档说明**

本文档中的风格规范为 *PyCharm v2018* 后的默认风格规范

所有规范都可通过查看 *PyCharm* 的滚动条区域判断是否通过

大部分规范都可通过自动格式化功能进行自动重构：`Code -> Format Code`

导入自动优化：`Code -> Optimize Imports`

-------

## 分号

* 不要在行尾加分号, 也不要用分号将两条命令放在同一行.

## 行长度

* 每行不超过 **120** 个字符

  *例外:*

    1.  长的导入模块语句
    2.  注释里的URL

## 缩进

* 用4个空格来缩进代码

* 绝对不要用tab, 也不要tab和空格混用. 对于行连接的情况, 你应该要么垂直对齐换行的元素(见 `行长度`
部分的示例), 或者使用4空格的悬挂式缩进(这时第一行不应该有参数):

``` python
  Yes:   # Aligned with opening delimiter
         foo = long_function_name(var_one, var_two,
                                  var_three, var_four)

         # Aligned with opening delimiter in a dictionary
         foo = {
             long_dictionary_key: value1 +
                                  value2,
             ...
         }

         # 4-space hanging indent; nothing on first line
         foo = long_function_name(
             var_one, var_two, var_three,
             var_four)

         # 4-space hanging indent in a dictionary
         foo = {
             long_dictionary_key:
                 long_dictionary_value,
             ...
         }
```

``` python
  No:    # Stuff on first line forbidden
        foo = long_function_name(var_one, var_two,
            var_three, var_four)

        # 2-space hanging indent forbidden
        foo = long_function_name(
          var_one, var_two, var_three,
          var_four)
```

## 空行

顶级定义之间空两行, 方法定义之间空一行

* 顶级定义之间空两行, 比如函数或者类定义.
* 类中的方法定义之间空一行.
* 函数或方法中, 某些地方要是你觉得合适,就空一行.

## 括号

* 宁缺毋滥的使用括号

* 除非是用于实现行连接, 否则不要在返回语句或条件语句中使用括号. 不过在元组两边使用括号是可以的.

``` python
    Yes: if foo:
             bar()

         while x:
             x = bar()

         if x and y:
             bar()

         if (not x) and y:
             bar()

         if not x:
             bar()

         return foo

         for (x, y) in dict.items():
             ...
```

``` python
    No:  if (x):
             bar()
         if not(x):
             bar()
         return (foo)
```

## 空格

按照标准的排版规范来使用标点两边的空格

* 括号内不要有空格.

``` python
    Yes: spam(ham[1], {eggs: 2}, [])
```

``` python
    No:  spam( ham[ 1 ], { eggs: 2 }, [ ] )
```

* 不要在逗号, 分号, 冒号前面加空格, 但应该在它们后面加(除了在行尾).

``` python
    Yes: if x == 4:
             print x, y
         x, y = y, x
```

``` python
    No:  if x == 4 :
             print x , y
         x , y = y , x
```

* 参数列表, 索引或切片的左括号前不应加空格.

``` python
    Yes: spam(1)
```

``` python
    No: spam (1)
```

``` python
    Yes: dict['key'] = list[index]
```

``` python
    No:  dict ['key'] = list [index]
```

* 在二元操作符两边都加上一个空格, 比如赋值(=), 比较(==, \<, \>, \!=, \<\>, \<=, \>=, in, not in, is, is not), 布尔(and, or, not).

  * 至于算术操作符两边的空格该如何使用, 需要你自己好好判断.
  * 不过两侧务必要保持一致.

``` python
    Yes: x == 1
```

``` python
    No:  x<1
```

* 当'='用于指示关键字参数或默认参数值时, 不要在其两侧使用空格.

``` python
    Yes: def complex(real, imag=0.0):
             return magic(r=real, i=imag)
```

``` python
    No:  def complex(real, imag = 0.0):
             return magic(r = real, i = imag)
```

* 不要用空格来垂直对齐多行间的标记, 因为这会成为维护的负担(适用于:, \#, =等):

``` python
    Yes:
         foo = 1000  # comment
         long_name = 2  # comment that should not be aligned

         dictionary = {
             "foo": 1,
             "long_name": 2,
             }
```

``` python
    No:
         foo       = 1000  # comment
         long_name = 2     # comment that should not be aligned

         dictionary = {
             "foo"      : 1,
             "long_name": 2,
             }
```

## 导入格式 ( import )

**使用Pycharm的导入优化**

* 使用包（package）的绝对路径。无论是否处于一个包中，都禁止使用相对路径import。因为这样做可能导致对同一模块加载两次

* 每个导入应该独占一行

``` python
    Yes: import os
         import sys
```

``` python
    No:  import os, sys
```

* 导入总应该放在文件顶部, 位于模块注释和文档字符串之后, 模块全局变量和常量之前.

* 导入应该按照从最通用到最不通用的顺序分组:

1.  标准库导入
2.  第三方库导入
3.  应用程序指定导入

* 每种分组中, 应该根据每个模块的完整包路径按字典序排序, 忽略大小写.

``` python
    import foo
    from foo import bar
    from foo.bar import baz
    from foo.bar import Quux
    from Foob import ar
```

## 语句

每个语句应该独占一行

``` python
    No:
      if foo: bar(foo)
      else:   baz(foo)

      try:               bar(foo)
      except ValueError: baz(foo)

      try:
          bar(foo)
      except ValueError: baz(foo)
```
