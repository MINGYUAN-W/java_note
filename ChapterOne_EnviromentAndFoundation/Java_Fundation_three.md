### 三、日期时间类

#### 1>System类

1、System类提供的public static long currentTimesMills()用来返回当前时间与1970.1.1 0时0分0秒以毫秒为单位的时间差。 此方法适用于计算时间差

#### 2>Date类

**1、构造方法**

Date()使用Date类的无参数构造方法创建的对象可以获取本地的当前时间

Date(long date)

**2、常用方法**

getTime()      返回一个long型的值

toString()

#### 3>SimpleDateFormat类

**1、易于国际化，更通用**

**2、方法：**

- 格式化1：日期----->文本  使用SimpleDateFormat()方法

```java
SimpleDateFormat sdf = new SimpleDateFormat();
String date = sdf.format(new Date());
System.out.println(date) 
```

- 格式化2：日期----->文本  使用有形参的构造器  指定形式可参考API文档

```java
SimpleDateFormat sdf1 = new SimpleDateFormat("yyyy-MM-dd hh:mm:ss")
String date = sdf.format(new Date());
System.out.println(date) 
```

- 解析：文本------>日期

```java
Date date1 = sdf.parse("xxxxxx")
```

#### 4>Calendar类

Calendar是一个抽象基类，主要用于完成日期字段之间相互操作的功能

1、获取Calendar实例的方法

- 使用Calendar.getInstance()方法
- 调用它的子类GregorianCalendar的构造器

2、方法

<img src="https://github.com/MINGYUAN-W/java_note/raw/master/pictures/ChapterOne_EnviromentAndFoundation/Calendar_Method.png" style="zoom:50%;" />

#### 5>LocalDate类

##### 1、LocalDate类常用方法

- static LocalDate now()

​               构造一个表示当前日期的对象

- static LocalDate of(int year, int month, int day)

​               构造一个表示给定日期的对象

- int getYear()
- int getMonthValue()
- in getDayOfMonth()

​               得到当前日期的年、月、日

- DayOfWeek getDayOfWeek

​               得到当前日期是星期几，作为DayOfWeek类的一个实例返回，调用getValue来得到1~7之间的一个数字，表示这是星期几，1表示是星期一，7表示星期日

- LocalDate plusDays(int n)
- LocalDate minusDays(int n)

​               生成当前日期之后或者之前的n天的日期

##### 2、实战实例

写一个程序输出当前月的日历：

如下格式：

<img src="https://github.com/MINGYUAN-W/java_note/raw/master/pictures/ChapterOne_EnviromentAndFoundation/LocalDate_instance.jpg" style="zoom:80%;" />

​       当前日期用一个*来标记

代码如下：

```java
import java.time.DayOfWeek;
import java.time.LocalDate;

public class CalenderTest {
    public static void main(String[] args) {
        LocalDate date = LocalDate.now();

        int today = date.getDayOfMonth();
        int month = date.getMonthValue();

        date = date.minusDays(today - 1);
        DayOfWeek weekday = date.getDayOfWeek();
        int wd = weekday.getValue();

   String[] str = new String []{"Mon","Tue","Wed","Thu","Fri","Sat","Sun"};
        for(int i = 0;i < 7;i++) {
            if (i == 6) {
                System.out.println(str[i]);
                continue;
            }
            System.out.print(str[i]+"   ");
        }

        for(int i = 1;i < wd;i++)
            System.out.print("      ");

        while(date.getMonthValue() == month){
            System.out.print(String.format("%-2d",date.getDayOfMonth()));
            if(date.getDayOfMonth() == today)
                System.out.print("*   ");
            else
                System.out.print("    ");

            date = date.plusDays(1);
            if(date.getDayOfWeek().getValue() == 1)
                System.out.println();
        }
    }
}
```

### 四、浅谈Math类

#### 1、BigDecimal

<img src="https://github.com/MINGYUAN-W/java_note/raw/master/pictures/ChapterOne_EnviromentAndFoundation/BigDecimal.png" style="zoom:50%;" />![](https://github.com/MINGYUAN-W/java_note/raw/master/pictures/ChapterOne_EnviromentAndFoundation/BigInteger.png)

#### 2、BigInteger

![](https://github.com/MINGYUAN-W/java_note/raw/master/pictures/ChapterOne_EnviromentAndFoundation/BigInteger.png)

### 五、输入与输出

#### 1>输入

##### 系统输入样例

```java
import java.util.Scanner;

public class InputTest {
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        int n = s.nextInt();           //输入整数用nextInt()方法
        String str = s.next();         //输入字符串用next()方法
        double m = s.nextDouble();     //输入浮点数：1、double类型用nextDouble()方法
        float f = s.nextFloat();       //2、float类型用nextFloat()方法
        //下面介绍如何获取一个字符
        //因为Scanner类并没有提供获取字符的方法，所以我们可以利用String类的方法
        String str1 = s.next();        //输入一个字符
        char c = str1.charAt(0);
    }
}
```



#### 2>输出

**1、格式化输出**

如果我们要输出小数，并且希望限制它小数点后的个数以及，所占的代码单元数。

可以使用如下几种方法：

- 

```java
double s = 6666.666666;
//我们希望它输出小数点后三位 并且占6个代码单元，左对齐
System.out.println(String.format("%6.3f",s));
//注意：String的format的是一种静态的方法
```

可以看到，他的格式化的方式和转换符和C语言中的printf的用法有很大的相似性

- 接下来介绍的一种方法，是和C语言很相似的

```java
ystem.out.printf("%6.3f",s);
//还可以使用逗号标志作为间隔符
System.out.printf("%,9.3f",s)
//此时的输出为： 6,666.333
```

**注意：**

a.转换符与C语言中的一致

b.标识符：