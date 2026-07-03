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

```
String a = "Java";
String b = "Java";

System.out.println(a == b);      // true
System.out.println(a.equals(b)); // true
```

## Array

### Declearation

```java
String[] a = new String[3];
String b[] = new String[3];

// Declear and Assign value
String c[] = {"1", "2", "3"};
String[] d = {"1", "2"};
String e[] = new String[]{"1", "2", "3"};
String[] f = new String[]{"1", "2"};

//Error 
String[] g;
g = {"1"}; //Error
g = new String[]{"1"};//Correct
```
### 长度固定 

超出长度报下标错误 `ArrayIndexOutOfBoundsException`


## ArrayList

### remove

> 有两种删除方法 根据下表int以及根据对象Object

会删除第一个匹配的Object


## StringBuilder

### property

线程不安全，可变, 非synchronize 常用单线程字符串拼接

### capacity 

默认16 首次扩容为2 * N + 2 第二次直接扩容到字符串长度


## StringBuffer

### Property
线程安全 可变 Synchronized

## Text Block 三个双引号

```Java
String html = """
              <html>
                <body>
                  <p>Hello</p>
                </body>
              </html>
              """;
```

> Text Block 的开始 """ 后面必须换行。

```Java
String masion = """ foo """; //Error: 
```