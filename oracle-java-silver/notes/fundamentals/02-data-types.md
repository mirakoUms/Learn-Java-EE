# Data Types

## 变量 variable

- int a = 12;    // 十进制 12
- int b = 012;   // 八进制 10
- int c = 0b1010; // 二进制 10
- int d = 0xA;   // 十六进制 10

### 作用域

| 类型                     | 位置              | 有没有默认值    |
| ---------------------- | --------------- | --------- |
| 实例变量 instance variable | 类中，方法外，非 static | 有默认值      |
| 静态变量 static variable   | 类中，方法外，static   | 有默认值      |
| 局部变量 local variable    | 方法内部            | **没有默认值** |

```java
class Test {
    int a;          // 实例变量，默认值 0
    static int b;   // static变量，默认值 0

    public static void main(String[] args) {
        int c;      // 局部变量，没有默认值
        System.out.println(c); // 编译错误
    }
}
```


## String

### Immutable

对String操作不会更变原本的值 而是返回新的字符串

```java
String a = "test";
a.concat("ing");
a.replaceAll("t","a");

System.out.println(a); // test

System.out.println(a.concat("ing")); // testing    
System.out.println(a.replaceAll("t","a")); // aesa    
```

而StringBuilder是可变的mutable


### 字符串字面量会进入 String Pool。

```java
String a = "Java";
String b = "Java";

System.out.println(a == b);      // true
System.out.println(a.equals(b)); // true
```

## Array

### Declaration

```java
String[] a = new String[3];
String b[] = new String[3];

// Declare and assign value
String c[] = {"1", "2", "3"};
String[] d = {"1", "2"};
String e[] = new String[]{"1", "2", "3"};
String[] f = new String[]{"1", "2"};

// Error
String[] g;
g = {"1"}; // Error
g = new String[]{"1"}; // Correct
```
### 长度固定 

超出长度报下标错误 `ArrayIndexOutOfBoundsException`

### 二维数组初始化

> 数组创建时，如果不用 {} 初始化器，第一维长度必须指定。

- 初始化创建

```Java
// 大括号初始化器
String i[][] = new String[][]{{"1", "2"}};
// 简略：String i[][] = {{"1", "2"}};
String[][] j = new String[][]{{"1", "2"}};
// 简略：String[][] j = {{"1", "2"}};

// 或者正常创建
String l[][] = new String[2][]; // 必须明确维度 dimension 
l[0] = new String[]{"1"};
l[1] = new String[]{"1", "3"};
l[2] = new String[]{"1", "3"}; // 执行错误 
```

## ArrayList

### remove

> 有两种删除方法：根据下标 `remove(int index)`，以及根据对象 `remove(Object o)`。

```java
ArrayList<Integer> list = new ArrayList<>(List.of(1, 2, 3));

list.remove(1);                  // 删除 index 1，也就是元素 2
list.remove(Integer.valueOf(1)); // 删除对象 1
```

`remove(Object o)` 会删除第一个匹配的对象。


## StringBuilder

### property

线程不安全、可变、非 synchronized，常用于单线程字符串拼接。

### capacity 

默认16 首次扩容为2 * N + 2 第二次直接扩容到字符串长度


## StringBuffer

### Property
线程安全 可变 Synchronized

## Text Block 三个双引号

```java
String html = """
              <html>
                <body>
                  <p>Hello</p>
                </body>
              </html>
              """;
```

> Text Block 的开始 """ 后面必须换行。

```java
String message = """ foo """; // Error: opening delimiter 后面必须换行
```

## var

> Java 10 的新功能

- 使用必须初始化

- 不可以同时声明 

```Java
var v1, v2 = 100;//'var' is not allowed in a compound declaration
var v1 = 10, v2 = 20; //'var' is not allowed in a compound declaration
```

- var 根据接受数据的object自动判断类型 所以不能 `var v1 = null`
