## 四、一些常用类的介绍和方法（浅谈）

接下来，我们学习一些常用类，当然此处只是浅谈，到了后面的学习会介绍关于这些类的更深的知识

### **一、String类**

String代表不可变的字符序列，底层用字符数组存放，是不可更改的。从概念上讲，java字符串就是<u>**Unicode字符序列**</u>。java没有内置的字符串类型，而是在标准类库中提供了一个<u>**预定义类**</u>，很自然的叫做String。每个双引号括起来的字符串都是String的一个实例。

#### 1>String类常用构造方法

```javascript
String s1 = new String();

String s2 = new String(String 4);

String s3 = new String(char[] a);

String s4 = new String(char[] a,int startindex,int count);
```

#### 2>String类的内存解析

<img src="https://github.com/MINGYUAN-W/java_note/raw/master/pictures/ChapterOne_EnviromentAndFoundation/java_string_memory_parsing.jpg" style="zoom:60%;" />

#### 3>子串

String类的substring方法可以从一个较大的字符串提取出一个子串。例如：

```javascript
String all = String.join("/","S","M","L","XL","XXL");
// all = "S/M/L/XL/XXL"
```

**其中substring方法的参数：**两个参数表示的是要提取子串所在的区间，要注意的是，是一个左闭右开的区间。 就如上面的例子：参数（0，3）表示从下标0（包括下标0）到下标3（不包括下标3）之内的字符串.【详细可参考后面的方法介绍】

#### 4>拼接，间隔符，复制

##### 1、可以使用连接符 + 

##### 2、如果需要把多个字符串放在一起，用一个界定符分隔，可以使用静态的join方法：

```java
String all = String.join("/","S","M","L","XL","XXL");
// all = "S/M/L/XL/XXL"
```

##### 3、java11中，还提供了一个repeat方法：

```java
String repeated = "Java".repeat(3);//repeated = "JavaJavaJava"
```

其中 repeat的参数是要复制字符串的次数

#### 5>检测字符串是否相等

##### 1、使用equals方法

```java
String s = "java";
s.equals(t);//t是另一个字符串变量
//若s与t相等 返回true 不同 则返回false
//注意的是：调用equals的对象也可以是一个字符串面量，如：
"java".equals(t);
```

##### 2、糟糕的“==”

- 在java中 == 符号只能是检测两个字符串的存储位置是否相等。当然，若两个字符串的存储位置相同，则它们就是同一个字符串，必然相等。但是，注意如下的例子

```java
String greeting = "Hello";
if(greeting == "Hello")
//此时括号内的条件就是true
if(greeting.substring(0,3) == "Hel")
//此时括号内的条件就是false
```

- <u>**重点：再往深了说，因为java虚拟机实际上只有字符串面量是共享的，而+ 或者 substring 等操作得到的字符串并不共享，所以一般不要用 == 来判断两个字符串是否相等**</u>

#### **6>常用的String中的方法**

- char charAt(int index)

​            返回指定下标的代码单元

- int codePointAt(int index)

​             返回指定位置开始的码点

- int compareTo(String other)

​             按照字典顺序，如果字符串位于other之前，返回一个负数。相等返回0。位于other之后，返回正数。

- boolean empty()
- boolean blank()

​              如果字符串为空或者由空格组成，返回true

- boolean equals(String s)

​               判断字符串是否相等，相等返回true，不相等返回false

- boolean equalsIgnoreCase(String other)

​               忽略大小写，来比较两个字符串是否相等

- boolean startsWith(String prefix)
- boolean endsWith(String suffix)

​               如果字符串以prefix开始或以suffix结束，返回true

- int indexOf(String str)
- int indexOf(String str, int fromIndex)

​               返回与字符串str相同的第一个子串开始的位置。从0或索引fromIndex开始寻找，若没有则返回-1

- int lastIndexOf(String str)

- int lastIndexOf(String str, int fromIndex)

​               返回与字符串str相同的最后一个子串开始的位置。从原始字符串末尾或索引fromIndex开始寻找，若没有则返回-1

- int length()

​              返回字符串代码单元的个数（即字符串长度）

- String replace(CharSequence oldString,CharSequence newString)

​              返回一个新的字符串。这个字符串用newString代替了原来字符串中所有的oldString。可以用String或者StringBuilder对象作为CharSequence的参数

- String substring(int beginIndex)
- String substring(int beginIndex , int endIndex)

返回一个新字符串，这个字符串是原字符串从beginIndex到字符串末尾或endIndex-1所有的代码单元 

- String toLowerCase()
- String toUpperCase()

​              返回一个新字符串，这个字符串将原始字符串中的大写字母改为小写字母，或者将原始字符串中的所有小写字母改写为大写字母

- String trim()
- String strip()

​               返回一个新字符串，这个字符串将删除原始字符串头部和尾部小于U+0020的字符（trim）或空格（strip）

- join方法和repeat方法

- pubic boolean regionMatches(int firstStart,String other,int other Start ,int length)

  判断当前字符串从firstStart开始的子串与另一个other字符串的otherStart开始 length长度的字串是否相等

- public String concat(String str) 

  连接str字符串

- public String[] split(String regex) 

  按照regex将当前字符串拆分，拆分为多个字符串，整体返回值为   String[]

#### 7>字符串与字节数组以及字符串与字符数组间的转换

##### 1、字符串------>字节数组：调用getBytes()

##### 2、字节数组------>字符串：调用字符串的构造器

##### 3、字符串----->字符数组：调用字符串的getCharArray()

##### 4、字符数组------>字符串：调用字符串的构造器

### 二、StringBuffer类和StringBuilder类

#### 1>StringBuffer类

##### 1、StringBuffer代表可变的字符序列

##### 2、StringBuffer常用方法

- StringBuffer ()

构造一个空的字符串构造器

- int length()

返回构造器或缓冲器中的代码单元数量

- StringBuffer append(String this)

追加一个字符串并返回this

- StringBuffer append(char c)

追加一个代码单元并返回this

- void setCharAt(int i , char c)

将第i个代码单元设置为c

- StringBuffer insert(int offset , String str)

在offset位置插入一个字符串并返回this

- StringBuffer insert(int offset , char c)

在offset位置插入一个代码单元并返回this

- StringBuffer delete(int startIndex , int endIndex)

删除偏移量从startIndex到endIndex-1的代码单元并返回this

- StringBuffer reverse()

导致此字符序列被序列的反向替换。

- String toString()

返回一个与构造器或缓冲器相同的字符串

- 查  charAt(int index)   indexOf(String str)  substring(int start,int end)  

  第一个：在index位置上的字符是什么

  第二个：字符串str的开头位于哪个位置                     第三个：提取子串

#### 2>StringBuilder

##### 1、可变的字符序列，是JDK5.0新加的 ,<u>**线程不安全 但效率高于StringBuffer**</u>

##### 2、常用方法也如上

- StringBuilder ()

构造一个空的字符串构造器

- int length()

返回构造器或缓冲器中的代码单元数量

- StringBuilder append(String this)

追加一个字符串并返回this

- StringBuilder append(char c)

追加一个代码单元并返回this

- void setCharAt(int i , char c)

将第i个代码单元设置为c

+ StringBuilder insert(int offset , String str)

在offset位置插入一个字符串并返回this

- StringBuilder insert(int offset , char c)

在offset位置插入一个代码单元并返回this

- StringBuilder delete(int startIndex , int endIndex)

删除偏移量从startIndex到endIndex-1的代码单元并返回this

- StringBuilder reverse()

导致此字符序列被序列的反向替换。

- String toString()

返回一个与构造器或缓冲器相同的字符串

