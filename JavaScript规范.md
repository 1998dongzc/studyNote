# JavaScript规范

#### 1.变量提前声明。

#### 2.不适用localStorage和SessionStorage。

#### 3.常规下数值采用十进制。

#### 4.switch语法每一个条件必须带有break关键字，每一个switch带有default默认条件。

#### 5.for循环的条件变量，必须在for条件中运算。

#### 6.方法复杂度不能太高，不能超过10，使方法功能不能太复杂。

#### 7.不使用IE浏览器的条件注释。

####  8.不使用关键字命名变量。

#### 9.非关键变量特殊情况 不重写外部域中的变量。

#### 10.不适用内置函数eval(),使用自定义的功能。

#### 11.带有花括号的语法如if，for，while等语法一行或多行代码块都要使用{}，提高代码可读性。

#### 12.if、for、while、switch和try之间不相互嵌套，提高代码可读性。

#### 13. 判断变量是否为NaN，不使用===NaN,使用Number.isNaN()。

#### 14.调用函数时，参数应按正确的顺序传递。

#### 15.delete可以删除对象的属性值，但对于数组时会删除某一个索引的值，但是该索引位置会有一个控制，数组的索引不会被更新。

使用以下方法

Array.prototype.splice - 增加/删除 指定位置元素
Array.prototype.pop - 删除 数组末尾位置元素
Array.prototype.shift - 删除 数组开始位置元素

#### 16.eval和arguments不能用来赋值或绑定，会修改其用法本意。

#### 17.编写函数，出现有无默认值和有默认值参数时，无默认值顺序在前，否则会报NaN错误。

#### 18.key-value形式，不重复存入相同的key导致代码误读性。

#### 19.setters函数不应该有返回值。

#### 20.注意==、!=和===、!==的区别。
> ==、!= 自动转换类型  ===、!==类型不同就直接返回false

#### 21.使用++ -- 自增自减时不给对象重新复制如 a=a++。

#### 22.尽量使用=== !== 比较符。

#### 23.对列表遍历时，能过滤数据就过滤数据。

#### 24.if while中只有判断 没有其他运算代码。

#### 25.尽量折叠合并 if。

#### 26.函数不应参数过多，参数过多时应用结构体包装。

#### 27.函数使用return返回值后不应再有语句。

#### 28.删除或注释空代码语句。

#### 29.只有while、for等循环才能使用label标签，并通过break labelName跳转。

#### 30.源文件中不能有重复的代码，删除掉重复的代码。

#### 31.提高阅读性，一行中不出现多个语句。

#### 32.定义函数中的参数，如不使用参数，删除对应参数。

#### 33.变量和函数不应重新声明。

#### 34.变量不能自己给自己赋值。

