# JAVA语言基础知识

## **一、java运行核心机制**

1、java是运行在一个java虚拟机上——jvm。jvm是一个虚拟的机，具有指令集并使用不同的储存区域。负责执行指令，管理数据、内存、寄存器。

2、对于不同的平台，有不同的虚拟机。

3、java虚拟机机制屏蔽了底层运行平台的差别，实现了“一次编译，到处运行”。

4、编译执行过程如下：


$$
\color{red}{    .java--->(通过javac.exe编译) .class--->(通过java.exe执行)不同系统上的jvm}
$$

## **二、基本知识**

###  1>java是由一个一个类构成的。

下面给一段java程序

- 如下：

```javascript
class HelloWorld{
     //这是main方法，它是程序的入口。
     public static void main(String[] args){
        /*
        这是程序的输出语句
        格式如下 System.out.println();
        */
        System.out.println("Hello Java!");
    }
}
```



注意一：模版。类中可以用main方法（主方法），格式是固定的，public static void main(String[] args).  main是程序的入口。方法内是程序的执行部分

注意二：注释可以检测bug所在行

注意三：print不需要换行 加上ln换行

注意四：多个类，允许存在于同一个源文件中。**但是，编译出来的，有几个类就会对应生成几个class文件**

**注意五：public是个关键字，可以修饰类 如 public class\**\*。若用public修饰了一个类，则这个类可以用在别的类里，而且，文件名必须与这个类名一样。并且 一个源文件中，最多只有一个类用public声明。**

### 2>注释

#### 1、普通的解释 与c语言一致。

#### 2、文档注释:格式如下

```javascript
/**
@author 指定java程序的作者
@version 指定源文件的版本
@param 方法的参数说明信息
*/
```

注释内容可以被JDK中的Javadoc工具所解析，生成一套以网页文件形式体现的该程序的说明文档。

操作方式：

......................javadoc -d mydoc(此处是建立一个名为mydoc的文件夹) -author -version  (文件名).java

**注意：必须有public声明的类**

## **三、基本语法**

### **1>关键字**

**定义**：被java语言赋予了特殊含义，用作专门用途的字符串。

**特点**：无小写。

1.用于定义**<u>数据类型</u>**的关键字：int  class boolean  interface  enum  long void  float  byte  double  short  char

2.用于定义**<u>数据类型值</u>**的关键字：true  false  null

3.用于定义**<u>流程控制</u>**的关键字：if  else     switch  case  default  while  do  for  do break  continue  return

### **2>标识符**

**定义**：java对各种变量，方法和类等要素命名时使用的字符串序列成为标识符。

**特点**：凡是自己可以起名字的地方都叫标识符。

**定义合法标志符的规则：**

①字母，数字，_ $组成

②数字不开头

③不可以使用关键字和保留字，但可以包含关键字和保留字。

④Java中严格区分大小写，但不限定长度。

⑤标识符不能包含空格。

**java命名规范：**

①包名：多单词组成时都用小写。

②类名，接口名：多单词组成时，所有单词的首字母都大写。

③变量名，方法名：多单词组成时，第一个单词首字母小写，第二个单词开始的每个单词首字母都大写。

Ⅳ常量名：所有字母都大写，多单词时用下划线连接。

### **3>变量**

#### 变量的分类——数据类型

##### 1、基本数据类型：

 Ⅰ

**数值型**：整型，浮点型（java里 float定义的数字后要加一个F）

 Ⅱ

**字符**：

- char定义单个字符（中文，英文。。。。），String定义字符串   
- 字符常量以Unicode值储存，Unicode码。
- 占两个字节

Ⅲ

**布尔**（boolean）

- java中不能以0和非0代替true和false

##### 2、引用数据类型

Ⅰ**类**（字符串在这里）

Ⅱ**接口**

Ⅲ**数组**

- 注：a.类型转化

​               b.同类型容量小的值可以向容量大的值转换。

​               c.整型向浮点型转化。

​               d.字符型向整形转化。

Ⅳ

**自动类型转化**：（不考虑boolean 只考虑char byte short int long float double）

- **注意：**byte，short只能向int转换。byte不能向short转化。即，只要short，byte，char之间做运算，包括自己之间，都向int转化.

Ⅴ

**强制类型转化**：容量大向容量小转化

```javascript
long l1=12345L;
int m1=(int)l1;
```

- **注意：**会造成精度损失（去高位，取低位）

Ⅵ

**字符串与基本数据类型之间的运算**：只能是连接运算:+。其结果仍为一个字符串。

### **4>运算符**

#### 1.逻辑运算符

- &和&&的区别：&不管左端是否是真，右端都会运算。&&左端是假，右端就不会运算。
- | 和 || 区别与上同理

#### 2.位运算符

- \>>   >>>的区别：前者是有符号右移  后者无符号右移   有符号是指，最高位是1则补1 是0则补0.
- 交换俩数字的新方法：m，n    m=m^n;n=m^n(  (m^n)^n=m  );m=m^n(  (m^n)^m=n   );
-  手动操作转换16进制wei代码：

```javascript
m=i&15(获取i的最低四位)

//大于十时的思想：（char）(m-10+'a')  //将m转化为对应的16进制
 String k1=(m>9)?m+"":(char)(m-10+'a'); 
 接下来，再往高四位看，要做的就是将m右移四位。再次与15&运算             
 i>>4;
 z=i&15;
String k2=(z>9)?z+"":(char)(m-10+'a');
```



### **5>数组**

#### 1、java 数组的定义以及特征：

- 数组是多个<u>**相同数据类型**</u>的组合，实现对这些数据的统一管理。
- 数组中的元素可以是<u>**任何数据类型**</u>，包括基本数据类型和引用数据类型。
- 数组属于引用类型，<u>**数组型数据类型是对象(object)**</u>，数组中的每个元素相当于该对象的成员变量。

#### 2、如何定义一个数组

```javascript
String[] names; //1.数组的声明
String names[];
int[] scores;
//2.初始化分为静态初始化和动态初始化
//2.1 静态初始化:初始化数组与给数组元素赋值同时进行
names=new String[]{"李云龙","楚云飞","政委"}；
//2.2动态初始化：初始化数组与给数组元素赋值分开进行
scores=new int[4];
```

#### 3、调用相应的数组元素

```javascript
scores[0]=87;
scores[1]=89;
scores[2]=99;
scores[3]=98;
```



#### 4、数组的长度：通过length属性

```javascript
System.out.println(names.length);
System.out.println(scores.length);
```



#### 5、遍历数组中的元素

用for循环，C中的方法。(还有一种for的each循环（强循环）我们到集合部分再进行讲解)

#### 6、数组的默认初始化值

- 对于byte short int long 而言：创建数组以后默认值为0（即使一个也不初始化，此处与C不同）
- 对于float  double而言，默认值是0.0
- 对于char而言 默认值是空格
- 对于Boolean而言 默认值为false
- 对于引用类型变量构成的数组，默认值是null

#### 7、数组的内存结构解析

##### 1.java的内存

<img src="https://github.com/MINGYUAN-W/java_note/blob/master/pictures/ChapterOne_EnviromentAndFoundation/java_memory_parsing.png?raw=true" style="zoom:50%;" />

##### 2.java数组的内存

<img src="https://github.com/MINGYUAN-W/java_note/blob/master/pictures/ChapterOne_EnviromentAndFoundation/java_array_memory_parsing_one.png?raw=true" style="zoom:50%;" />

##### 3.二维数组

- 代码引例

```javascript
//1、二维数组的初始化
  //静态初始化：
  int[][] scores=new int[][]{{1,2,3},{3,4,5},{6}}
  //动态初始化：
  String[][] names=new String[6][5];//动态初始化方式一
  String[][] names=new String[6][];
  names[0]=new String[5];
  names[0]=new String[7];
  names[0]=new String[8];
  names[0]=new String[3];
  names[0]=new String[9];
  names[0]=new String[6];
  //以上为动态初始化方式二
//2.引用具体的某个元素
//3.遍历用嵌套循环
//4.长度属性仍可用
//5.元素长度和数组长度要区分
```

- 二维数组内存解析

<img src="https://github.com/MINGYUAN-W/java_note/blob/master/pictures/ChapterOne_EnviromentAndFoundation/java_array_memory_parsing_two.png?raw=true" style="zoom:50%;" />

#### 8、数组的一些常用方法

- static String toString(xxx[] a)

​           返回包含a中元素的一个字符串，这些元素用中括号包围，并用逗号分隔。在这个方法以及后面的方法中，

​           数组元素类型xxx可以是int  long  short  char  byte  boolean  float  double

- static xxx[] copyOf(xxx[] a, int end)

- static xxx[] copyOfRange(xxx[] a, int start, int end)

​           返回与a类型相同的一个数组，其长度为length或者end-start，数组元素为a的值。

​           如果end大于a.length，结果会填充0或false值  

- static void sort(xxx[] a)

​            使用优化的快速排序算法对数组进行排序

- static int binarySearch(xxx[] a , xxx v)

- static int binarySearch(xxx[] a, int start, int end, xxx v)

​            使用二分查找法在有序数组a中查找值v  如果找到值v 则返回相应的下标 否则返回一个负数值r                     

​             -r-1是v插入的位置（为保证a有序）

- static void fill(xxx[] a, xxx v)

​            将数组所有元素设置为v

- static boolean equals(xxx[] a, xxx[] b)

​            如果两个数组大小相同，并且下标相同的元素都对应相等，返回true