# 对象与类

##  一、面向对象思想的概述

### 1>面向对象与面向过程：

- 二者都是一种思想，面向对象是相对于面向过程而言的。面向过程强调的是功能行为。面向对象，将功能封装进对象，强调具备了功能的对象。
- 面向对象更加强调运用人类在日常的逻辑中采用的思想方法与原则，如抽象，分类，继承，聚合，多态等。
- 面向对象的三大特征：封装，继承，多态。

```java
/*
*理解一(根据面向对象来理解)：人开门
面向过程：人 打开 门
面向对象：  对象：人，门
人{
    打开（门）{
        门.开开（）;
    }
}
门{
    开开（）{
        
    }
}


*理解二（根据面向过程来理解）：人把大象装进冰箱
面向过程：1、打开冰箱2、把大象放进去3、关闭冰箱门
面向对象：  对象： 人，大象，冰箱。
人{
    打开（冰箱）{
        冰箱.开开（）
    }
    操作（大象）{
        大象.进入（冰箱）
    }
    关闭（冰箱）{
        冰箱.合上（）
    }
}
大象{
    进入（冰箱）{}
}
冰箱{
    开开（）{} 
    合上（）{}
}
*/
```

### 2>面向对象（OOP）程序设计概述

  1、 面向对象的程序是由**对象**组成的，每个对象包含**对用户公开的特定功能部分**和**隐藏的实现部分。**

> 传统的面向过程程序设计（结构化程序设计）通过设计一系列的过程（算法）来求解问题。一旦确定了这些过程，就要开始考虑存储数据的适当方式。（这就是常说的：算法+数据结构=程序）。明确的来说，编程，首先要确定如何操作数据，然后决定如何组织数据的结构，以便于操作数据。**但是，OOP却调换了这个次序，将数据放在第一位，然后再考虑操作数据的算法**

2、**总结**

- 程序员从执行者转化成指挥者
- 完成需求时

​                      ➡先去找具有所需功能的对象来用。

​                      ➡如果该对象不存在，那么创建一个更具有所需功能的对象

​                      ➡这样简化开发并提高复用。

- class类和object对象时面向对象的核心概念

​                      ➡类是对一类事物的描述，是抽象的、概念上的定义。

​                      ➡对象是实际存在的该类事物的每个个体，因而也称实例

- 万事万物皆对象
- **面向对象设计程序的重点是类的设计**
- **定义类其实是定义类中的成员（成员变量和成员方法）**

3、**面向对象思想的落地法则一：**

- 设计类并设计类的成员（成员变量以及成员方法）。
- 通过类，来创建类的对象（类的实例化）。
- 通过"对象.属性   对象.方法"来调用，完成相应的功能。



## 二、对象与类

### 1>类

#### **1.1 java类及类的成员**

##### 1.1.1 描述类的两种方法：属性、行为。

- 属性对应类中的成员变量

​       属性=成员变量

- 行为对应类中的成员方法

​        成员方法=函数

例一：

```java
//类是抽象的
class person{
    //1、属性
    String name;
    int age;
    boolean sex;
    
    //2、方法
    public void eat(){
        System.out.println("人吃饭")；
    }
    public void sleep(){
        System.out.println("人睡觉");
    }
          //获取属性
    public String getName(){
        return name;
    }
    public void setName(String n){
        name=n;
    }
    public void info(){
        eat();
        sleep();
        System.out.println("name: ")
    }
}
```

例二：

```java
public class zoo{
    public static void main(String[] args){
        //基本数据类型的声明
        int i=10;
        //类的实例化(引用数据类型) a1就是一个实实在在的对象
        Animal a1 = new Ainimal();
        //通过对象调用属性
        a1.name=“花花”；
        a1.age=3;
       System.out.println("");
       //通过对象调用方法
       a1.eat();
       a1.sleep(); 
    }
}

class Animal{
    //1.属性
    String name;
    int age;
    
    //2.方法
    public void eat(){
        System.out.println("动物进食");
    }
    public String getName(){
        return name;
    }
    public void setName(String n){
        name=n;
    }
}
```

#### 1.2 类的内存解析

<img src="https://github.com/MINGYUAN-W/java_note/blob/master/pictures/ChapterTwo_ObjectAndClass/Java_class_memory_parsing.png?raw=true" style="zoom:50%;" />![](https://github.com/MINGYUAN-W/java_note/blob/master/pictures/ChapterTwo_ObjectAndClass/Value_Transfer_Memory_Parsing.png?raw=true)

#### 1.3 java类的属性（成员变量）与局部变量

##### 1.3.1 相同点：

- 遵循变量声明的格式
- 都有作用域

##### 1.3.2 不同点：

- 声明位置的不同。

  ​                               **成员变量：**声明在类里，方法外

​                                      **局部变量：**声明在方法内，方法的形参部分，代码块内。

-  **成员变量**的修饰符有四个：public private protected 缺省

​        **局部变量**没有修饰符：与所在方法的修饰符相同。

- 初始化值：一定会有初始化值

​                                      **成员变量：**如果在声明的时候，不显示的赋值，不同的数据类型会有不同的默认初始化值

​                                      **局部变量：** <u>**一定要显示的赋值。（局部变量没有默认初始化值)**</u>

- 二者内存中存放的位置不同：**成员变量**存在于堆空间中；**局部变量：**栈空间中

#### 1.4 类的方法:提供某种功能的实现

- 例：

```java
public void eat(){}
public String getName(){}
public void setName(String n){}
```

**格式：** 权限修饰符 返回值类型（void ： 无返回值/具体的返回值类型）

返回值将会返回给当前的对象

类中的方法可以访问类中的成员变量

##### 1.4.1 重载

```java
public void see(){}
public void see(int i){}
public void see(int i,int m){}
public void see(String str){}
public void see(int[] n){}
```

以上的代码就是一个方法的重载

- **重载的定义：**有着相同的方法名，相同的返回类型，不同的参数（个数不同，类型不同），就构成了重载。

再往深了说，Java中，重载可以用于一切方法，包括构造方法（构造器）。

​       **注释：**要完整的描述一个方法，需要指定方法名以及参数类型。叫做这个方法的**签名**。然而返回类型不是签名的一部分，也就是说，不能有两个名字相同、参数类型也相同但却有不同返回类型的方法。



##### 1.4.2 方法参数

###### 1.4.2.1 形参与实参

- 形参：方法声明时的括号里的参数

- 实参：调用方法时实际传入的参数

###### 1.4.2.2 java中的传递机制------值传递

- 值传递和地址传递：

​       **值传递**：表示方法接收的是调用者提供的值。

​       **地址传递**：表示方法接收的是调用者提供的变量地址（典型的就是C语言中的指针）

- 参数为基本数据类型的值传递：

​       假如要写一个方法，这个方法的功能是交换 a b 的值

```java
  public class pc{
    public static void main(String[] args){
        int a = 1;
        int b = 2;
        pc.swap(a.b);
        //此时a b的值仍然没有交换，为什么呢？ 我们来看看他的内存解析
    }
    //这个是错误的写法
    public static void swap(int m,int n){
        int temp = m;
        m = n;
        n = temp;
    }
}
```


​      内存解析如下：

<img src="https://github.com/MINGYUAN-W/java_note/blob/master/pictures/ChapterTwo_ObjectAndClass/Value_Transfer_Memory_Parsing.png?raw=true" style="zoom:60%;" />

​      **那我们考虑一个有效的写法**：

```java
//我们可以把要交换的一对值写进一个类里，并且把这个类实例化
//把实例化的对象（实例化与对象的内容后面讲解）作为一个参数传入交换方法，或者也可以直接调换
public class test{
    public static void main(String[] args){
        value v1 = new value();
        //1.调用交换方法
        swap(v1);
        //2.直接调换
        int temp = v1.a;
        v1.a = v1.b;
        v1.b = temp;
    }
    public static void swap(value v){
        int temp = v.a;
        v.a = v.b;
        v.b = temp;
    }
}
class value{
    int a = 1;
    int b = 2;
}
```

内存解析如下：

<img src="https://github.com/MINGYUAN-W/java_note/blob/master/pictures/ChapterTwo_ObjectAndClass/Value_Transfer_Memory_Parsing_r1.png?raw=true" style="zoom:67%;" />

<img src="https://github.com/MINGYUAN-W/java_note/blob/master/pictures/ChapterTwo_ObjectAndClass/Value_Transfer_Memory_Parsing_r2.png?raw=true" style="zoom:67%;" />

<img src="https://github.com/MINGYUAN-W/java_note/blob/master/pictures/ChapterTwo_ObjectAndClass/Value_Transfer_Memory_Parsing_r3.png?raw=true" style="zoom:67%;" />

**那直接交换的内存解析是什么呢？不妨动手画一画吧！**

#### 1.5 类的构造器：

 类的第三个成员：构造器（构造方法）。

##### 1.5.1构造器的作用：

- 创建对象
- 给创建的对象的属性赋值
- 初始化属性

```java
person() s=new person();
//其中 new后面的person()就是构造器
```



##### 1.5.2 空构造器

设计类时，若不显示声明类的构造器的话，程序会默认提供一个空的构造器

构造器写法如下

```java
//构造器函数名与类名一样
public person(String n){
    name=n;
}
```



##### 1.5.3 一旦显示的定义类的构造器，那么默认的构造器就不再提供。

##### 1.5.4 格式

​      声明类的构造器，    

​      格式：  权限修饰符 类名（形参）{}

##### 1.5.5 构造器的重载

​     类的构造器之间也可以构成重载

##### 1.5.6 属性的赋值的先后顺序：

​       属性的默认初始化值，属性的显示赋值（要在构造器赋值的前面），构造器的初始化值，通过对象的.方法的方式给属性赋值。

#### 1.6 this关键字

- 可以用来修饰属性、方法、构造器
- this理解为当前对象或当前正在创建的对象：this.name，this.show（）；
- this(形参):可以用来显示的调用当前类的重载的构造器，**必须放在首行**。
- tihs()使用次数有限制

```java
class person{
   int age;
   String name;
   boolean man;
   
   public person(String name){
   //this关键字来调用构造器，必须放在首行
   this();//就是在调用person的空参构造器
   //this修饰属性
   this.name = name//前者的name是这个类的属性 后者的name是参数
   }
   
   public person(){
   //this 修饰方法
   this.age = 18;
   this.man = true;
   }
}
```



#### 1.7 static------静态字段与静态方法

**static 静态的 可以用来修饰属性 方法 代码块（初始化块） 内部类**

##### 1.7.1 修饰属性（类变量）：

- 由类创建的所有的对象，都**共用这一个属性**，也可以这样说，静态变量属于类，而不属于任何单个的对象。
- 当其中一个对象对此属性进行修改，会导致其他对象对此属性的一个调用。
- **类变量随着类的加载而加载（不依据实体对象的存在）**
- 静态的变量可以直接通过**“类.类变量”**的形式来调用
- 类变量的加载是要早于对象的，所有当有对象以后，**可以“对象.类变量”  但是“类.实例变量”是不行的**
- 类变量存在于**静态域**中

##### 2、修饰方法（类方法）：

- 随着类的加载而加载，在内存中也是独一份
- 可以直接通过**“类.方法”**的方式来调用
- 内部可以调用**静态的属性**或者**静态的方法**，而不能调用**非静态的属性或者方法**。反之，**非静态的方法**是可以调用**静态的属性或者方法**

#### **1.8 关键字final**

最终的，可以用来修饰类，属性，方法

##### **1.8.1 修饰类，这个类不可以被继承。**

##### **1.8.2 修饰方法，这个方法不可以被重写**

##### **1.8.3 final修饰属性，此属性就是一个常量，用大写字符去表示**

​      此常量在那里赋值：a.不能使用默认初始化 b.可以显示的赋值，代码块，构造器

##### 1.8.4 static final 修饰的是 全常量

#### 1.9 **初始化块（类的第四个成员）的应用**

代码块是什么呢？如下：

```java
class pc{
//1.非静态代码块
{
    //some operation
}
 //2.静态代码块
 static
 {
    //some operation
 }
}
```



##### 1.9.1 关于属性赋值的几种操作方法：

- 通过默认的初始化
- 通过显示的初始化或代码块初始化（按照顺序结构执行）
- 通过构造器
- 通过方法
- 通过代码块：如果有修饰符，修饰符只能是static

##### 1.9.2 分类：

- 非静态代码块：

​               a.可以对类的属性（静态，非静态）进行赋值，同时也可以调用本类声明的方法

​               b.可以有输出语句

​               **c.一个类可以有多个非静态的代码块，多个代码块之间按照顺序结构执行**

​               d.每创建一个类，非静态的代码块就加载一次

​               **e.非静态的代码块的执行要早于构造器**

​               **f.代码块与实例字段按照顺序执行**

- 静态代码块（修饰符为static）：

​              a.与静态的属性和方法一样，只加载一次。

​              **b.加载早于非静态的**

​              **c.多个静态代码块之间按照顺序执行**

​              d.静态的代码块中只能执行静态的结构（类属性，类方法）

​              e.随着类的加载而加载

##### 1.9.3 代码内含构造器与代码块的处理步骤：

- [x] 如果构造器的第一行调用了另一个构造器，则基于所提供的参数执行第二个构造器
- [x] 否则

- 所有数据字段初始化为其默认值（0、false或null）
- 按照在类声明中出现的顺序，执行所有字段初始化方法和初始化块

- [x] 执行构造器主体代码

### 2>对象与实例化

#### 2.1 对象与对象变量

##### 2.1.1 对象与对象变量

- 先看如下代码：

```java
public class PersonTest{
    public static void main(String[] args){
        Person person = new Person();
        person person1 = new Person("Jack","男")
    }
}
class Person{
    String name;
    String sex;
    
    public Person(){
    }
    public Person(String name,String sex){
        this.name = name;
        this.sex = sex;
    }
    public void eat(){
    }
    public void act(){
    }
}
```



- 对象变量： 代码中的 **Person person**    **Person person1**    的 person person1 都是对象变量
- 对象：代码中的new出来的就是对象，这个对象就是由构造器创建的。
- 我们来看看 他的内存解析：

<img src="https://github.com/MINGYUAN-W/java_note/blob/master/pictures/ChapterTwo_ObjectAndClass/Object_Memory_Parsing_r3.png?raw=true" style="zoom:67%;" />

##### 2.1.2 类的实例化

在Java程序设计语言中，要用构造器构造新实例。构造器是一种特殊的方法，用来构造并初始化对象。<u>**创造对象的这个过程就称为类的实例化的过程**</u>。

#### 2.2 用var声明局部变量

在java10中如果可以从变量的初始值推导出他们的类型，那么可以用var关键字声明这个卡局部变量。

例如：

```java
Person person = new Person();
//我们可以写成如下代码
var person = new Person();
```

从现在开始倘若无需了解任何Java API 就能从等号右边明显看出类型，在这种情况下我们都将使用var表示法。

但是，<u>**我们不会对数值类型使用var，如 int long double**</u>。

### 3>类之间的三大关系

#### 3.1 依赖

> ​        依赖是一种最明显的、最常见的关系。简单来说，如果一个类的方法使用或操作另一个类的对象，我们可以说一个类依赖于另一个类。我们编写了一个账户类和订单类，而我们要考虑到在账户下订单的时候，订单类会访问账户类的对象来查看信用状态，由此，构成了订单类使用或操作了账户类，所以订单类依赖账户类。
>
> ​        应该注意的是，应该尽可能的减少相互依赖的类减至最少。智利的关键是，如果类A不知道B的存在，它就不会关心B的任何改变（这意味着B的改变不会导致A产生任何bug）。用软件工程的术语来讲，就是尽可能减少类之间的“耦合”。

#### 3.2 聚合

>​        简单来说就是 一个类包含着另一个类

#### 3.3 继承

> ​        继承是面向对象中很重要的一个概念，我们会在后面深入讨论。
>
> ​        所以我们在这里留一个悬念，到后面我们深入交流~~~