# Command Log

This file records shell commands executed while organizing this repository.

Format:

- `Time`: local timestamp from the current machine.
- `Working directory`: directory where the command was run.
- `Command`: command text.
- `Output`: stdout and stderr captured from the command.

## 2026-07-07 21:26:14 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
git status --short
```

Output:

```text
 D "AWS SAA/SAA-C03  \351\242\230\347\233\256\344\270\255\346\226\207\347\211\210.pdf"
 D "AWS SAA/dammy.dammy"
 D "Oracle Java Silver/0123.pdf"
 D "Oracle Java Silver/ClassObjectMethod/basic.md"
 D "Oracle Java Silver/LogicCalculation/basic.md"
 D "Oracle Java Silver/ObjectOrientation/AbstractClassBasic.md"
 D "Oracle Java Silver/ObjectOrientation/EncapsulationBasic.md"
 D "Oracle Java Silver/ObjectOrientation/InheriantanceBasic.md"
 D "Oracle Java Silver/ObjectOrientation/InterfaceBasic.md"
 D "Oracle Java Silver/ObjectOrientation/NewFeatureBasic.md"
 D "Oracle Java Silver/ObjectOrientation/Override&OverloadBasic"
 D "Oracle Java Silver/ObjectOrientation/PolymorphismBasic.md"
 D "Oracle Java Silver/ObjectOrientation/TypeCastBasic.md"
 D "Oracle Java Silver/dataType/basic.md"
 D "Oracle Java Silver/javaBasic/basic.md"
 M README.md
?? aws-saa/
?? log/
?? oracle-java-silver/
```

## 2026-07-07 21:26:31 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
Get-Content -Tail 40 log\command-log.md
```

Output:

```text

- `Time`: local timestamp from the current machine.
- `Working directory`: directory where the command was run.
- `Command`: command text.
- `Output`: stdout and stderr captured from the command.

## 2026-07-07 21:26:14 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
git status --short
```

Output:

```text
 D "AWS SAA/SAA-C03  \351\242\230\347\233\256\344\270\255\346\226\207\347\211\210.pdf"
 D "AWS SAA/dammy.dammy"
 D "Oracle Java Silver/0123.pdf"
 D "Oracle Java Silver/ClassObjectMethod/basic.md"
 D "Oracle Java Silver/LogicCalculation/basic.md"
 D "Oracle Java Silver/ObjectOrientation/AbstractClassBasic.md"
 D "Oracle Java Silver/ObjectOrientation/EncapsulationBasic.md"
 D "Oracle Java Silver/ObjectOrientation/InheriantanceBasic.md"
 D "Oracle Java Silver/ObjectOrientation/InterfaceBasic.md"
 D "Oracle Java Silver/ObjectOrientation/NewFeatureBasic.md"
 D "Oracle Java Silver/ObjectOrientation/Override&OverloadBasic"
 D "Oracle Java Silver/ObjectOrientation/PolymorphismBasic.md"
 D "Oracle Java Silver/ObjectOrientation/TypeCastBasic.md"
 D "Oracle Java Silver/dataType/basic.md"
 D "Oracle Java Silver/javaBasic/basic.md"
 M README.md
?? aws-saa/
?? log/
?? oracle-java-silver/
```
```

## 2026-07-07 21:27:22 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
Get-ChildItem -Path "oracle-java-silver\notes" -Recurse -File -Filter *.md | Sort-Object FullName | ForEach-Object {
    $first = Get-Content -LiteralPath $_.FullName -Encoding UTF8 -TotalCount 1
    $lines = (Get-Content -LiteralPath $_.FullName -Encoding UTF8 | Measure-Object -Line).Lines
    [PSCustomObject]@{ File = Resolve-Path -Relative $_.FullName; Lines = $lines; FirstLine = $first }
} | Format-Table -AutoSize
```

Output:

```text

File                                                     Lines FirstLine                                               
----                                                     ----- ---------                                               
.\oracle-java-silver\notes\01-java-basics.md               104 # Java Basics                                           
.\oracle-java-silver\notes\02-data-types.md                 84 # Data Types                                            
.\oracle-java-silver\notes\03-operators-and-flow.md         43 # Operators and Flow                                    
.\oracle-java-silver\notes\04-classes-objects-methods.md    26 # Classes, Objects, and Methods                         
.\oracle-java-silver\notes\05-encapsulation.md              29 # Encapsulation 封装                                      
.\oracle-java-silver\notes\06-inheritance.md                73 # 继承 (Inheritance)：允许子类继承父类的属性和方法，建立 is-a（是什么）的关系。这极大...
.\oracle-java-silver\notes\07-polymorphism.md               52 # 父类引用 指向子类对象                                           
.\oracle-java-silver\notes\08-type-casting.md                1 # 类型转换                                                  
.\oracle-java-silver\notes\09-abstract-classes.md           23 # 抽象类                                                   
.\oracle-java-silver\notes\10-interfaces.md                 64 # interface 接口                                          
.\oracle-java-silver\notes\11-overriding-overloading.md     27 # Overriding and Overloading                            
.\oracle-java-silver\notes\12-java-17-features.md          126 # Java 17 Features
```

## 2026-07-07 21:27:32 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
rg -n "a$|defalut|Declear|overide|privtae|nesssarily|cant|instance of|排他伦理和|synchronize|Class foo|public Bird extends|A\.super\.test|Optional<String> name = Optional\.of\(name\)|masion" oracle-java-silver/notes
```

Output:

```text
oracle-java-silver/notes\10-interfaces.md:22:public Bird extends Animal implements Flyable {
oracle-java-silver/notes\10-interfaces.md:75:    - 选择特定接口的static： 方法体内写`A.super.test()`
oracle-java-silver/notes\09-abstract-classes.md:15:> It is a compile-time error if a method declaration that contains the keyword abstract also contains any one of the keywords private, static, final, native, strictfp, or synchronized.
oracle-java-silver/notes\05-encapsulation.md:37:    - 如果构造器为privtae，那么将无法在类外使用这个构造器
oracle-java-silver/notes\03-operators-and-flow.md:9:- ^ 异或 排他伦理和
oracle-java-silver/notes\03-operators-and-flow.md:34:- 基本用法 `obj instance of` 返回boolean
oracle-java-silver/notes\03-operators-and-flow.md:63:    defalut -> 3;
oracle-java-silver/notes\02-data-types.md:64:### Declearation
oracle-java-silver/notes\02-data-types.md:70:// Declear and Assign value
oracle-java-silver/notes\02-data-types.md:99:线程不安全，可变, 非synchronize 常用单线程字符串拼接
oracle-java-silver/notes\02-data-types.md:126:String masion = """ foo """; //Error: 
oracle-java-silver/notes\01-java-basics.md:63:Optional<String> name = Optional.of(name); //　nullpointerException
oracle-java-silver/notes\01-java-basics.md:85:final int a; // correct: not nesssarily assign value to it when assert final 
oracle-java-silver/notes\01-java-basics.md:91:final void foo(); // error: final method cannot be overide
oracle-java-silver/notes\01-java-basics.md:93:final Class foo() {
oracle-java-silver/notes\01-java-basics.md:97:final Class foo2 extends foo() {
oracle-java-silver/notes\01-java-basics.md:98:    // error: final Class cant not be extended
```

## 2026-07-07 21:27:43 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
Get-Content -Raw -Encoding UTF8 "oracle-java-silver/notes/08-type-casting.md"
```

Output:

```text
# 类型转换
```

## 2026-07-07 21:27:52 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
Get-Content -Raw -Encoding UTF8 "oracle-java-silver/notes/01-java-basics.md"
```

Output:

```text
# Java Basics

### Wrapper Class ラッパクラス
- byte -> Byte
- int -> Integer
- *char -> Character*
- *short -> Short*
- ....


### Serialization　シリアライゼーション

> 将对象序列化，用于数据传输

- `static`, `transient` 不会被序列化
```java
class User implements Serializable {
    static String school = "ABC"; //static 属于类，不属于对象本身，所以不会作为对象状态被保存。
    String name;
    transient String password;
}
```

- serialVersionUID

用来判断“保存时的类”和“读取时的类”版本是否兼容。反序列化时会用它验证发送方和接收方加载的类是否兼容；如果不兼容抛出 `InvalidClassException`。

```java

private static final long serialVersionUID = 1L;
```


### Optional

> first appear: Java 8

#### 创建 Optional
- 有值：Optional.of()

```java
Optional<String> opt = Optional.of("Java");
```

- 可能为 null：Optional.ofNullable()

```java
String name = null;
Optional<String> opt = Optional.ofNullable(name);
```

> 如果 name 是 null，就得到一个空的 Optional。

- 空 Optional：Optional.empty()

```java
Optional<String> opt = Optional.empty();
```

- 如果optional.of()传null的参数则空指针异常
```java
String name = null;
Optional<String> name = Optional.of(name); //　nullpointerException
```

### Fall Through

> Java 17 的 -> 写法不会 fall through

```java
// Java 17 新功能

int x = 1;

switch (x) {
    case 1 -> System.out.println("A");
    case 2 -> System.out.println("B");
    case 3 -> System.out.println("C");
}// 输出：A
```

### final

```java
final int a; // correct: not nesssarily assign value to it when assert final 
a = 10; // first time: correct
a = 20; // second time: error

final void foo();
@override
final void foo(); // error: final method cannot be overide

final Class foo() {

}

final Class foo2 extends foo() {
    // error: final Class cant not be extended
}
```

### intern

> Java 为了节省内存，相同的字符串字面量只保存一份
```java
String a = "Java";
String b = "Java";
```
          String Pool
      +-------------+
      |   "Java"    |
      +-------------+
          ▲      ▲
          │      │
          a      b

所以 a == b

> new String 
```java
String a = new String("Java");
```
            Heap
         +-----------+
    a -> | "Java"    |
         +-----------+

          String Pool
         +-----------+
         | "Java"    |
         +-----------+

> intern()
```java
String a = new String("Java");
a.intern();
```
- 去 String Pool 找有没有内容相同的字符串。
    - 有 → 返回 Pool 中那个对象。
    - 没有 → 把当前字符串加入 Pool，再返回 Pool 中的对象。


### a
```

## 2026-07-07 21:28:02 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
Get-Content -Raw -Encoding UTF8 "oracle-java-silver/notes/02-data-types.md"
```

Output:

```text
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
String masion = """ foo """; //Error: 
```
```

## 2026-07-07 21:28:11 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
Get-Content -Raw -Encoding UTF8 "oracle-java-silver/notes/03-operators-and-flow.md"
```

Output:

```text
# Operators and Flow

运算符与控制结构



## 逻辑
### 可以进行逻辑运算与位运算
- ^ 异或 排他伦理和
- & 按位与
- | 按位或
- ~ 按位取反 计算公式`~x == -x - 1`

> &和|的逻辑运算不会短路

### 移位运算
- basic
```java
System.out.println(6 << 2);// 0110 -> 0001 1000 24
System.out.println(-6 >> 2);// -1000 -> -0010 -2
// 无符号右移，英文叫 unsigned right shift。
System.out.println(-6 >>> 2);
// 11111111 11111111 11111111 11111010 -> 00111111 11111111 11111111 11111110　2**30 - 1 - 1 = 1073741822
```
- long 实际移动位数 = n % 64
```java
System.out.println(1L << 64); // 1
System.out.println(1L << 65); // 2
```
### instanceof

> 用来判断对象是不是某个类的实例

- 基本用法 `obj instance of` 返回boolean

- null instanceof 返回false -> null 不是任何类的实例

- obj必须是引用类型，不能是基本类型








## Switch

### 支持的数据类型

- 数字类以及各自的参照 int，byte, char, short
- String
- 枚举 enum

### java 17 新语法

- 执行多行最后用`yield`返回数据
- 不会fall through， 但可以多个情况放在一起处理
```java
int x = switch(1) {
    case 1, 2, 3 -> 1;
    case 4, 5 -> 2;
    defalut -> 3;
};
```
```

## 2026-07-07 21:28:22 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
Get-Content -Raw -Encoding UTF8 "oracle-java-silver/notes/10-interfaces.md"
```

Output:

```text
# interface 接口

## 定义

 ```java
 interface Flyable {
    void fly(); // 等同于 public abstract void fly();
    // 进行实现时不能省略public(不写默认范围为package private) 
 }
 ```

 ## 不能直接实例化 但是可以声明指向子类的引用型
 ```java
 // Flyable f = new Flyable(); // Error
Flyable f = new Bird(); // bird实现flyable
 ```

## 规则

- 必须先继承 后实现
 ```java
public Bird extends Animal implements Flyable {
    // class body
}
 ```

- 可以实现多个接口
 ```java
public Birds implements Flyable, Layeggable {
    // class body
}
 ```

 ## 变量

 > 接口中的字段隐式是 public static final，并且接口字段必须有初始化值。

并且命名习惯大写 加 下划线分割符 如 
```java
interface Flyable {
    public static final float FLY_SPEED = 27.3f;
    // class body
}
 ```


## default 方法

> default 方法可以给接口增加新功能，同时保持和旧实现类的兼容性。

```java
interface Walkable {
    default void walk() {
        System.out.println("walking"); // 定义并默认了walk方法
    }
}

class Human implements Walkable {
}

public class Main {
    public static void main(String[] args) {
        Human h = new Human();
        h.walk();
    }
}
```

## static方法

- 类似普通的Class中static方法 不通过实现类名调用，而是通过接口名调用

- 实现多个接口时 存在相同static方法
    - 重写该方法
    - 选择特定接口的static： 方法体内写`A.super.test()`

## private方法 

- 不能被实现类实现 用于default或者static方法共同部分的包装

## 父类的方法优先于接口的方法

> 继承体系独立性

## 接口的继承

- 接口可以继承 实现类则必须实现接口父类以及接口类中全部的抽象方法

- 接口可以继承自多个接口 相较于类只能继承一个类
```

## 2026-07-07 21:28:33 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
Get-Content -Raw -Encoding UTF8 "oracle-java-silver/notes/06-inheritance.md"
```

Output:

```text
# 继承 (Inheritance)：允许子类继承父类的属性和方法，建立 is-a（是什么）的关系。这极大地提高了代码的复用性，并支持基类的行为扩展。

## 只允许单类继承

Class Dog extends Animal, Mammal {} // 则会报错

## 所有类都继承自Object

- 所以都可以用以下Object的方法 即使没有重写
    - toString()
    - equals()
    - hashCode()
    - getClass()

## 父类没有无参构造器时，子类的声明必须指定存在的父类构造器

```java
class Animal {
    Animal(String name) {
        System.out.println("init");
    }
}
class Dog extends Animal {
    Dog() {
        super("dog"); // 这里必须指定name
        System.out.println("init");
    }
}

```

## super关键字 可以访问父类成员 或者构造器

```java
class Parent {
    String name = "Parent";

    void print() {
        System.out.println("Parent method");
    }
}

class Child extends Parent {
    String name = "Child";

    void test() {
        super(); // 调用父类无参构造放大
        System.out.println(name);
        System.out.println(super.name);
        super.print(); // 调用成员package private方法 但是无法访问private方法
    }
}

public class Main {
    public static void main(String[] args) {
        new Child().test();
    }
}
```

## private 方法无法被override

## final class无法被继承
- final class：类不能被继承
- final method：方法不能被重写
- final variable：变量不能再次赋值

## 父类引用可以指向子类对象 但无法使用子类定义的新方法

Parent p = new Child(); // Correct
p.cry();                // Error, cry对于Child是新方法 而引用p指向的对象中没有这个方法


## 继承和初始化顺序

> static init:
```java
class Room {
    static {
        System.out.println("Static init");
    }
}
```
> init
```java
class Room {
    {
        System.out.println("Static init");
    }
}
```

- 父类static -> 子类static -> 父类init -> 父类constructor -> 子类init -> 子类constructor 
- static代码块在一次执行者仅执行一次
```

## 2026-07-07 21:28:43 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
Get-Content -Raw -Encoding UTF8 "oracle-java-silver/notes/07-polymorphism.md"
```

Output:

```text
# 父类引用 指向子类对象

> 编译时看引用类型 运行时看实际类型

> Parent p = new child();

## 适用范围

> 实例方法的重写

```java
class Animal {
    String name = "animal";

    void print() {
        System.out.println("Animal method");
    }
}
class Dog extends Animal {
    String name = "dog";

    void print() {
        System.out.println("Dog method");
    }
}
Animal a = new Dog();

System.out.println(a.name);// 字段没有多态，运行时看引用类型因此输出Animal
a.print();                  // Dog重写了Animal的print方法 看实际类型输出 Dog Method
```

## 多态的用法

```java
class Animal {
    void speak() {
        System.out.println("animal");
    }
}
class Dog extends Animal {
    void speak() {
        System.out.println("dog");
    }
}
class Cat extends Animal {
    void speak() {
        System.out.println("cat");
    }
}

class Zoo {
    void makeSound(Animal a) {
        a.speak();      // Dog、Cat也是Animal 实际运行时会参照各自重写的speak方法
    }
}
public class Main {
    public static void main(String[] args) {
        Zoo zoo = new Zoo();

        zoo.makeSound(new Dog());
        zoo.makeSound(new Cat());
    }
}
```
```

## 2026-07-07 21:28:52 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
Get-Content -Raw -Encoding UTF8 "oracle-java-silver/notes/04-classes-objects-methods.md"
```

Output:

```text
# Classes, Objects, and Methods

## constructor

### 默认构造器 

> 如果类中没有写任何构造器，编译器会自动生成一个无参构造器。
> 只要写了任意构造器，默认构造器就不会生成


### 重构构造器

### this()/super()

- `this()` 用来在 同一个类内部复用构造器逻辑。

```java
class User {
    String name;
    int age;

    User() {
        this("unknown", 0);
    }

    User(String name) {
        this(name, 0);
    }

    User(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

- super() 用来调用 父类构造器




### 初始化顺序
```

## 2026-07-07 21:29:01 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
Get-Content -Raw -Encoding UTF8 "oracle-java-silver/notes/05-encapsulation.md"
```

Output:

```text
# Encapsulation 封装

## 可见性

- *private 字段只能在 Person 类内部访问。其他类（即使是子类）中即使创建对象也无法访问*
- 不加修饰符不等于public 在其他包的类中无法访问 (package private)
- protected 在其他包的子类中有条件的访问 非子类无法访问
- public 完全开放

## getter setter 

### getter暴露私有成员变量 

### setter控制实例化的成员变量值

```java
private String gender;

public void setGender(String gender) {
    if ("male".equals(gender) && "male".equals(gender)) {
        // 对不法值进行控制
        return;
    }
    this.gender = gender;
}
```


## Protected的访问范围

- *在不同包的子类中：不可以通过父类实例访问protected字段*
- 但是可以使用子类实例访问

## 构造器的访问权限

- 仍遵循以上原则
    - 如果构造器为privtae，那么将无法在类外使用这个构造器
    - 包外部使用构造器时 需要是public否则不可见

## 方法重写时

- 可以保持不变或者范围扩大 “无法从public到private”
- private 方法不能被重写
```

## 2026-07-07 21:29:10 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
Get-Content -Raw -Encoding UTF8 "oracle-java-silver/notes/09-abstract-classes.md"
```

Output:

```text
# 抽象类

## 抽象类也有自己的构造方法

- 但是自己无法实例化 所以构造方法给子类用

## 抽象类不能使用以下关键字进行声明

- final

abstract抽象需要进行重写，因此需要被继承，不可以用final同时修饰

## 抽象方法不能使用一下关键字声明

> It is a compile-time error if a method declaration that contains the keyword abstract also contains any one of the keywords private, static, final, native, strictfp, or synchronized.

```java
abstract static void test();   // 错
abstract final void test();    // 错
private abstract void test();  // 错
```

## 为什么与接口那么像

| 比较    | 抽象类              | 接口                          |
| ----- | ---------------- | --------------------------- |
| 关键字   | `abstract class` | `interface`                 |
| 继承/实现 | `extends`        | `implements`                |
| 数量    | 一个类只能继承一个父类      | 一个类可以实现多个接口                 |
| 实例变量  | 可以有普通实例变量        | 字段默认是 `public static final` |
| 构造方法  | 可以有              | 没有构造方法                      |
| 适合表达  | “是什么”            | “能做什么”                      |

> 抽象类定义对象是什么 接口则描述对象有哪些能力
```

## 2026-07-07 21:29:19 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
Get-Content -Raw -Encoding UTF8 "oracle-java-silver/notes/11-overriding-overloading.md"
```

Output:

```text
# Overriding and Overloading

## 重载调用的优先级

- 完全一致

- 范围扩展
如int和long

- 装箱
如long和Integer

- 不固定参数个数
如Integer和int...

## 关于null

### 匹配会优先到范围更小更具体的重载方法

如参数为null时 比起Object更优先调用参数类型为String的方法
*如果无法比较谁更加具体则会报错 比如Integer和String，因为两者不存在继承关系*

## static方法隐藏

> 子类定义了一个和父类 static 方法同名、同参数的方法时，它不是 override，而是把父类的 static 方法“隐藏”了。
因此按照引用类型的static方法进行执行

## 是重写还是重载
- 重载先在编译期决定
- 重写再在运行期决定

- 重载看引用类型 
- 重写看实际对象

## 和异常

- 重写时
    - 不能抛出更宽的 checked exception
    - 可以抛出更窄的 checked exception
    - 可以不抛出
    - RuntimeException 不受这个限制
```

## 2026-07-07 21:29:29 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
Get-Content -Raw -Encoding UTF8 "oracle-java-silver/notes/12-java-17-features.md"
```

Output:

```text
# Java 17 Features

## sealed Java17

> sealed class / sealed interface 用来限制哪些类或接口可以继承或实现它。

### 基本写法

```java
sealed class Animal permits Dog, Cat {
    // 只允许被Dog，Cat继承
}

class Dog extends Animal {
}

final class Cat extends Animal {
}
```

### 子类的作用域

> permitted subclass 必须直接继承 `sealed class`，并且必须正好使用 `final`、`sealed`、`non-sealed` 三者之一来说明后续继承规则。

- final

```java
sealed class Animal permits Dog {
}

final class Dog extends Animal {
    // Dog 不能再被继承。
}
class Poodle extends Dog { 
    // Error: the type Poodle cannot subclass the final class Dog
}
```

- sealed

> 可继承范围进一步缩小

```java
sealed class Animal permits Dog {
}

sealed class Dog extends Animal permits Poodle {
}

final class Poodle extends Dog {
}
```

- non-sealed

> 放开父类的继承限制

```java
sealed class Animal permits Dog {
    }

non-sealed class Dog extends Animal {
    // 放开限制
}

class Poodle extends Dog {
    }
```

> 但是不能随便声明:如果一个类被声明为 non-sealed，但它没有 sealed 直接父类或 sealed 直接父接口，就是编译错误。

```java
non-sealed class Dog {
    // Error: The non-sealed class Animal must have a sealed direct supertype
}
```

### sealed与接口

> interface 不能是 final，但可以是 sealed，用于限制子接口或实现类。
```java
sealed interface Flyable permits Furthered, Bird {
}
// 限制子类接口 此时不能是final 只能是sealed或non-sealed
non-sealed interface Furthered extends Flyable {
}
// 限制实现类 此时可以用final sealed 或者 non-sealed修饰
final class Bird implements Flyable {
}
```









## record java17

> record 会为每个组件自动声明 private final 字段、同名同类型的 public accessor、canonical constructor(包含全字段的标准构造器)、equals、hashCode、toString。

### 基本用法

```java
record Person(String name, int age) { //注意没有class关键字
}
```

会被转换成

```java
final class Person extends java.lang.Record {
    private final String name;
    private final int age;

    Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String name() {// 注意不是getName
        return name;
    }

    public int age() {
        return age;
    }

    public boolean equals(Object o) {
        // 自动生成
    }

    public int hashCode() {
        // 自动生成
    }

    public String toString() {
        // 自动生成
    }
}
```


### 继承

> record class 是隐式 final，所以不能显式继承 record class

```java
sealed class Animal permits Dog { }
record Dog(String name) extends Animal { } // 报错
```

### 实现接口

> record 不能继承别的类，因为它已经隐式继承 java.lang.Record，但可以实现一个或多个接口。

```java
record Bird(String name, ....) implements flyable,... { }
```

### 声明static实例变量

> record不能声明 instance variables，也不能有 instance initializer。

### 构造方法 compact constructor

> compact constructor 的参数由 record components 自动推导，并且在 compact constructor 结束时，参数会自动赋给对应的 private fields。

```java
record User(String name) {
    public User {
        name = name.toUpperCase();
    }
}
```

## sealed与record组合使用

> record class 可以出现在 sealed class/interface 的 permits 子句中；

```java
sealed interface Flyable permits Bird { }
record Bird(...) implements Flyable { } // 因为 record 隐式 final，很适合作为 sealed 类型的 permitted subclass。
```
```

## 2026-07-07 21:33:18 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
rg -n "a$|defalut|Declear|overide|privtae|nesssarily|cant|instance of|排他伦理和|synchronize|Class foo|public Bird extends|A\.super\.test|Optional<String> name = Optional\.of\(name\)|masion|class Dog extends Animal \{|record Bird\(String name, \.\.\.\.\)|implements flyable" oracle-java-silver/notes
```

Output:

```text
oracle-java-silver/notes\03-operators-and-flow.md:38:```java
oracle-java-silver/notes\02-data-types.md:53:```java
oracle-java-silver/notes\02-data-types.md:91:```java
oracle-java-silver/notes\02-data-types.md:105:线程不安全、可变、非 synchronized，常用于单线程字符串拼接。
oracle-java-silver/notes\01-java-basics.md:69:```java
oracle-java-silver/notes\01-java-basics.md:96:```java
oracle-java-silver/notes\01-java-basics.md:148:```java
oracle-java-silver/notes\04-classes-objects-methods.md:9:```java
oracle-java-silver/notes\04-classes-objects-methods.md:36:```java
oracle-java-silver/notes\04-classes-objects-methods.md:56:```java
oracle-java-silver/notes\04-classes-objects-methods.md:62:class Dog extends Animal {
oracle-java-silver/notes\04-classes-objects-methods.md:75:```java
oracle-java-silver/notes\05-encapsulation.md:20:```java
oracle-java-silver/notes\06-inheritance.md:7:```java
oracle-java-silver/notes\06-inheritance.md:27:class Dog extends Animal {
oracle-java-silver/notes\06-inheritance.md:38:```java
oracle-java-silver/notes\06-inheritance.md:81:```java
oracle-java-silver/notes\06-inheritance.md:98:```java
oracle-java-silver/notes\07-polymorphism.md:5:```java
oracle-java-silver/notes\07-polymorphism.md:21:class Dog extends Animal {
oracle-java-silver/notes\07-polymorphism.md:42:class Dog extends Animal {
oracle-java-silver/notes\08-type-casting.md:9:```java
oracle-java-silver/notes\08-type-casting.md:24:```java
oracle-java-silver/notes\08-type-casting.md:35:```java
oracle-java-silver/notes\08-type-casting.md:49:```java
oracle-java-silver/notes\08-type-casting.md:58:```java
oracle-java-silver/notes\08-type-casting.md:70:```java
oracle-java-silver/notes\09-abstract-classes.md:18:> It is a compile-time error if a method declaration that contains the keyword abstract also contains any one of the keywords private, static, final, native, strictfp, or synchronized.
oracle-java-silver/notes\10-interfaces.md:5:```java
oracle-java-silver/notes\10-interfaces.md:14:```java
oracle-java-silver/notes\10-interfaces.md:23:```java
oracle-java-silver/notes\10-interfaces.md:31:```java
oracle-java-silver/notes\10-interfaces.md:42:```java
oracle-java-silver/notes\10-interfaces.md:76:```java
oracle-java-silver/notes\10-interfaces.md:92:```java
oracle-java-silver/notes\10-interfaces.md:105:        A.super.test();
oracle-java-silver/notes\12-java-17-features.md:14:final class Dog extends Animal {
oracle-java-silver/notes\12-java-17-features.md:31:final class Dog extends Animal {
oracle-java-silver/notes\12-java-17-features.md:62:non-sealed class Dog extends Animal {
oracle-java-silver/notes\12-java-17-features.md:82:```java
oracle-java-silver/notes\12-java-17-features.md:151:```java
oracle-java-silver/notes\12-java-17-features.md:160:```java
oracle-java-silver/notes\12-java-17-features.md:168:```java
```

## 2026-07-07 21:33:49 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
New-Item -ItemType Directory -Force -Path "oracle-java-silver\notes\fundamentals", "oracle-java-silver\notes\object-oriented", "oracle-java-silver\notes\java-17" | Out-Null
Move-Item -LiteralPath "oracle-java-silver\notes\01-java-basics.md" -Destination "oracle-java-silver\notes\fundamentals\01-java-basics.md"
Move-Item -LiteralPath "oracle-java-silver\notes\02-data-types.md" -Destination "oracle-java-silver\notes\fundamentals\02-data-types.md"
Move-Item -LiteralPath "oracle-java-silver\notes\03-operators-and-flow.md" -Destination "oracle-java-silver\notes\fundamentals\03-operators-and-flow.md"
Move-Item -LiteralPath "oracle-java-silver\notes\04-classes-objects-methods.md" -Destination "oracle-java-silver\notes\fundamentals\04-classes-objects-methods.md"
Move-Item -LiteralPath "oracle-java-silver\notes\05-encapsulation.md" -Destination "oracle-java-silver\notes\object-oriented\05-encapsulation.md"
Move-Item -LiteralPath "oracle-java-silver\notes\06-inheritance.md" -Destination "oracle-java-silver\notes\object-oriented\06-inheritance.md"
Move-Item -LiteralPath "oracle-java-silver\notes\07-polymorphism.md" -Destination "oracle-java-silver\notes\object-oriented\07-polymorphism.md"
Move-Item -LiteralPath "oracle-java-silver\notes\08-type-casting.md" -Destination "oracle-java-silver\notes\object-oriented\08-type-casting.md"
Move-Item -LiteralPath "oracle-java-silver\notes\09-abstract-classes.md" -Destination "oracle-java-silver\notes\object-oriented\09-abstract-classes.md"
Move-Item -LiteralPath "oracle-java-silver\notes\10-interfaces.md" -Destination "oracle-java-silver\notes\object-oriented\10-interfaces.md"
Move-Item -LiteralPath "oracle-java-silver\notes\11-overriding-overloading.md" -Destination "oracle-java-silver\notes\object-oriented\11-overriding-overloading.md"
Move-Item -LiteralPath "oracle-java-silver\notes\12-java-17-features.md" -Destination "oracle-java-silver\notes\java-17\12-java-17-features.md"
```

Output:

```text
<no output>
```

## 2026-07-07 21:34:44 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
$results = New-Object System.Collections.Generic.List[string]
$results.Add('Files:')
$results.AddRange((rg --files | Sort-Object))
$results.Add('')
$results.Add('Note first lines:')
Get-ChildItem -Path "oracle-java-silver\notes" -Recurse -File -Filter *.md | Sort-Object FullName | ForEach-Object {
    $first = Get-Content -LiteralPath $_.FullName -Encoding UTF8 -TotalCount 1
    $results.Add(("{0} => {1}" -f (Resolve-Path -Relative $_.FullName), $first))
}
$results.Add('')
$results.Add('README link check:')
$linkIssues = New-Object System.Collections.Generic.List[string]
Get-ChildItem -Path . -Filter README.md -Recurse | Where-Object { $_.FullName -notmatch '\\.git\\' } | ForEach-Object {
    $base = Split-Path -Parent $_.FullName
    $content = Get-Content -Raw -Encoding UTF8 -LiteralPath $_.FullName
    [regex]::Matches($content, '\[[^\]]+\]\(([^)]+)\)') | ForEach-Object {
        $link = $_.Groups[1].Value
        if ($link -match '^(https?:|#)') { return }
        $target = $link -replace '^\./', ''
        $full = Join-Path $base $target
        if (-not (Test-Path -LiteralPath $full)) {
            $linkIssues.Add(("{0} -> {1}" -f (Resolve-Path -Relative $_.FullName), $link))
        }
    }
}
if ($linkIssues.Count -eq 0) { $results.Add('No broken local README links found.') } else { $results.AddRange($linkIssues) }
$results.Add('')
$results.Add('Known typo scan:')
$typos = (rg -n "defalut|Declear|overide|privtae|nesssarily|cant|instance of|排他伦理和|masion|implements flyable|record Bird\(String name, \.\.\.\.\)|Optional<String> name = Optional\.of\(name\)" oracle-java-silver/notes 2>$null | Out-String).TrimEnd()
if ([string]::IsNullOrWhiteSpace($typos)) { $results.Add('No known typo patterns found.') } else { $results.Add($typos) }
$results.Add('')
$results.Add('Git status:')
$results.AddRange((git status --short))
$results.Add('')
$results.Add('Diff stat:')
$results.AddRange((git diff --stat HEAD))
$results -join [Environment]::NewLine
```

Output:

```text
Files:

Note first lines:
.\oracle-java-silver\notes\fundamentals\01-java-basics.md => # Java Basics
.\oracle-java-silver\notes\fundamentals\02-data-types.md => # Data Types
.\oracle-java-silver\notes\fundamentals\03-operators-and-flow.md => # Operators and Flow
.\oracle-java-silver\notes\fundamentals\04-classes-objects-methods.md => # Classes, Objects, and Methods
.\oracle-java-silver\notes\java-17\12-java-17-features.md => # Java 17 Features
.\oracle-java-silver\notes\object-oriented\05-encapsulation.md => # Encapsulation 封装
.\oracle-java-silver\notes\object-oriented\06-inheritance.md => # Inheritance 继承
.\oracle-java-silver\notes\object-oriented\07-polymorphism.md => # Polymorphism 多态
.\oracle-java-silver\notes\object-oriented\08-type-casting.md => # Type Casting 类型转换
.\oracle-java-silver\notes\object-oriented\09-abstract-classes.md => # 抽象类
.\oracle-java-silver\notes\object-oriented\10-interfaces.md => # interface 接口
.\oracle-java-silver\notes\object-oriented\11-overriding-overloading.md => # Overriding and Overloading

README link check:
No broken local README links found.

Known typo scan:
No known typo patterns found.

Git status:

Diff stat:
```

## 2026-07-07 21:35:04 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
rg --files | Sort-Object
git status --short
git diff --stat HEAD
```

Output:

```text
aws-saa\README.md
aws-saa\resources\saa-c03-questions-zh.pdf
log\command-log.md
oracle-java-silver\notes\fundamentals\01-java-basics.md
oracle-java-silver\notes\fundamentals\02-data-types.md
oracle-java-silver\notes\fundamentals\03-operators-and-flow.md
oracle-java-silver\notes\fundamentals\04-classes-objects-methods.md
oracle-java-silver\notes\java-17\12-java-17-features.md
oracle-java-silver\notes\object-oriented\05-encapsulation.md
oracle-java-silver\notes\object-oriented\06-inheritance.md
oracle-java-silver\notes\object-oriented\07-polymorphism.md
oracle-java-silver\notes\object-oriented\08-type-casting.md
oracle-java-silver\notes\object-oriented\09-abstract-classes.md
oracle-java-silver\notes\object-oriented\10-interfaces.md
oracle-java-silver\notes\object-oriented\11-overriding-overloading.md
oracle-java-silver\README.md
oracle-java-silver\resources\oracle-java-silver-reference.pdf
README.md
 D "AWS SAA/SAA-C03  \351\242\230\347\233\256\344\270\255\346\226\207\347\211\210.pdf"
 D "AWS SAA/dammy.dammy"
 D "Oracle Java Silver/0123.pdf"
 D "Oracle Java Silver/ClassObjectMethod/basic.md"
 D "Oracle Java Silver/LogicCalculation/basic.md"
 D "Oracle Java Silver/ObjectOrientation/AbstractClassBasic.md"
 D "Oracle Java Silver/ObjectOrientation/EncapsulationBasic.md"
 D "Oracle Java Silver/ObjectOrientation/InheriantanceBasic.md"
 D "Oracle Java Silver/ObjectOrientation/InterfaceBasic.md"
 D "Oracle Java Silver/ObjectOrientation/NewFeatureBasic.md"
 D "Oracle Java Silver/ObjectOrientation/Override&OverloadBasic"
 D "Oracle Java Silver/ObjectOrientation/PolymorphismBasic.md"
 D "Oracle Java Silver/ObjectOrientation/TypeCastBasic.md"
 D "Oracle Java Silver/dataType/basic.md"
 D "Oracle Java Silver/javaBasic/basic.md"
 M README.md
?? aws-saa/
?? log/
?? oracle-java-silver/
 ...33\256\344\270\255\346\226\207\347\211\210.pdf" | Bin 6496769 -> 0 bytes
 AWS SAA/dammy.dammy                                |   0
 Oracle Java Silver/0123.pdf                        | Bin 27137223 -> 0 bytes
 Oracle Java Silver/ClassObjectMethod/basic.md      |  41 -----
 Oracle Java Silver/LogicCalculation/basic.md       |  63 -------
 .../ObjectOrientation/AbstractClassBasic.md        |  36 ----
 .../ObjectOrientation/EncapsulationBasic.md        |  43 -----
 .../ObjectOrientation/InheriantanceBasic.md        |  94 -----------
 .../ObjectOrientation/InterfaceBasic.md            |  89 ----------
 .../ObjectOrientation/NewFeatureBasic.md           | 184 ---------------------
 .../ObjectOrientation/Override&OverloadBasic       |  40 -----
 .../ObjectOrientation/PolymorphismBasic.md         |  66 --------
 .../ObjectOrientation/TypeCastBasic.md             |   2 -
 Oracle Java Silver/dataType/basic.md               | 125 --------------
 Oracle Java Silver/javaBasic/basic.md              | 141 ----------------
 README.md                                          |  15 +-
 16 files changed, 14 insertions(+), 925 deletions(-)
```

## 2026-07-07 21:35:23 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
$linkIssues = @()
Get-ChildItem -Path . -Filter README.md -Recurse | Where-Object { $_.FullName -notmatch '\\.git\\' } | ForEach-Object {
    $readme = $_
    $base = Split-Path -Parent $readme.FullName
    $content = Get-Content -Raw -Encoding UTF8 -LiteralPath $readme.FullName
    [regex]::Matches($content, '\[[^\]]+\]\(([^)]+)\)') | ForEach-Object {
        $link = $_.Groups[1].Value
        if ($link -match '^(https?:|#)') { return }
        $target = $link -replace '^\./', ''
        $full = Join-Path $base $target
        if (-not (Test-Path -LiteralPath $full)) {
            $linkIssues += "$(Resolve-Path -Relative $readme.FullName) -> $link"
        }
    }
}
if ($linkIssues.Count -eq 0) { 'No broken local README links found.' } else { $linkIssues }

$typos = rg -n "defalut|Declear|overide|privtae|nesssarily|cant|instance of|排他伦理和|masion|implements flyable|record Bird\(String name, \.\.\.\.\)|Optional<String> name = Optional\.of\(name\)" oracle-java-silver/notes
if ($LASTEXITCODE -eq 1) { 'No known typo patterns found.' }
```

Output:

```text
No broken local README links found.
No known typo patterns found.
```

## 2026-07-07 21:35:33 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
Get-Content -Tail 80 log\command-log.md
```

Output:

```text
oracle-java-silver\notes\object-oriented\08-type-casting.md
oracle-java-silver\notes\object-oriented\09-abstract-classes.md
oracle-java-silver\notes\object-oriented\10-interfaces.md
oracle-java-silver\notes\object-oriented\11-overriding-overloading.md
oracle-java-silver\README.md
oracle-java-silver\resources\oracle-java-silver-reference.pdf
README.md
 D "AWS SAA/SAA-C03  \351\242\230\347\233\256\344\270\255\346\226\207\347\211\210.pdf"
 D "AWS SAA/dammy.dammy"
 D "Oracle Java Silver/0123.pdf"
 D "Oracle Java Silver/ClassObjectMethod/basic.md"
 D "Oracle Java Silver/LogicCalculation/basic.md"
 D "Oracle Java Silver/ObjectOrientation/AbstractClassBasic.md"
 D "Oracle Java Silver/ObjectOrientation/EncapsulationBasic.md"
 D "Oracle Java Silver/ObjectOrientation/InheriantanceBasic.md"
 D "Oracle Java Silver/ObjectOrientation/InterfaceBasic.md"
 D "Oracle Java Silver/ObjectOrientation/NewFeatureBasic.md"
 D "Oracle Java Silver/ObjectOrientation/Override&OverloadBasic"
 D "Oracle Java Silver/ObjectOrientation/PolymorphismBasic.md"
 D "Oracle Java Silver/ObjectOrientation/TypeCastBasic.md"
 D "Oracle Java Silver/dataType/basic.md"
 D "Oracle Java Silver/javaBasic/basic.md"
 M README.md
?? aws-saa/
?? log/
?? oracle-java-silver/
 ...33\256\344\270\255\346\226\207\347\211\210.pdf" | Bin 6496769 -> 0 bytes
 AWS SAA/dammy.dammy                                |   0
 Oracle Java Silver/0123.pdf                        | Bin 27137223 -> 0 bytes
 Oracle Java Silver/ClassObjectMethod/basic.md      |  41 -----
 Oracle Java Silver/LogicCalculation/basic.md       |  63 -------
 .../ObjectOrientation/AbstractClassBasic.md        |  36 ----
 .../ObjectOrientation/EncapsulationBasic.md        |  43 -----
 .../ObjectOrientation/InheriantanceBasic.md        |  94 -----------
 .../ObjectOrientation/InterfaceBasic.md            |  89 ----------
 .../ObjectOrientation/NewFeatureBasic.md           | 184 ---------------------
 .../ObjectOrientation/Override&OverloadBasic       |  40 -----
 .../ObjectOrientation/PolymorphismBasic.md         |  66 --------
 .../ObjectOrientation/TypeCastBasic.md             |   2 -
 Oracle Java Silver/dataType/basic.md               | 125 --------------
 Oracle Java Silver/javaBasic/basic.md              | 141 ----------------
 README.md                                          |  15 +-
 16 files changed, 14 insertions(+), 925 deletions(-)
```

## 2026-07-07 21:35:23 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
$linkIssues = @()
Get-ChildItem -Path . -Filter README.md -Recurse | Where-Object { $_.FullName -notmatch '\\.git\\' } | ForEach-Object {
    $readme = $_
    $base = Split-Path -Parent $readme.FullName
    $content = Get-Content -Raw -Encoding UTF8 -LiteralPath $readme.FullName
    [regex]::Matches($content, '\[[^\]]+\]\(([^)]+)\)') | ForEach-Object {
        $link = $_.Groups[1].Value
        if ($link -match '^(https?:|#)') { return }
        $target = $link -replace '^\./', ''
        $full = Join-Path $base $target
        if (-not (Test-Path -LiteralPath $full)) {
            $linkIssues += "$(Resolve-Path -Relative $readme.FullName) -> $link"
        }
    }
}
if ($linkIssues.Count -eq 0) { 'No broken local README links found.' } else { $linkIssues }

$typos = rg -n "defalut|Declear|overide|privtae|nesssarily|cant|instance of|æŽ’ä»–ä¼¦ç†å’Œ|masion|implements flyable|record Bird\(String name, \.\.\.\.\)|Optional<String> name = Optional\.of\(name\)" oracle-java-silver/notes
if ($LASTEXITCODE -eq 1) { 'No known typo patterns found.' }
```

Output:

```text
No broken local README links found.
No known typo patterns found.
```
```

## 2026-07-07 21:37:22 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
git branch --show-current
```

Output:

```text
write/silver
```

## 2026-07-07 21:37:22 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
git status --short
```

Output:

```text
 D "AWS SAA/SAA-C03  \351\242\230\347\233\256\344\270\255\346\226\207\347\211\210.pdf"
 D "AWS SAA/dammy.dammy"
 D "Oracle Java Silver/0123.pdf"
 D "Oracle Java Silver/ClassObjectMethod/basic.md"
 D "Oracle Java Silver/LogicCalculation/basic.md"
 D "Oracle Java Silver/ObjectOrientation/AbstractClassBasic.md"
 D "Oracle Java Silver/ObjectOrientation/EncapsulationBasic.md"
 D "Oracle Java Silver/ObjectOrientation/InheriantanceBasic.md"
 D "Oracle Java Silver/ObjectOrientation/InterfaceBasic.md"
 D "Oracle Java Silver/ObjectOrientation/NewFeatureBasic.md"
 D "Oracle Java Silver/ObjectOrientation/Override&OverloadBasic"
 D "Oracle Java Silver/ObjectOrientation/PolymorphismBasic.md"
 D "Oracle Java Silver/ObjectOrientation/TypeCastBasic.md"
 D "Oracle Java Silver/dataType/basic.md"
 D "Oracle Java Silver/javaBasic/basic.md"
 M README.md
?? aws-saa/
?? log/
?? oracle-java-silver/
```

## 2026-07-07 21:38:02 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
git branch --show-current
```

Output:

```text
write/silver
Exit code: 0
```

## 2026-07-07 21:38:03 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
git status --short
```

Output:

```text
 D "AWS SAA/SAA-C03  \351\242\230\347\233\256\344\270\255\346\226\207\347\211\210.pdf"
 D "AWS SAA/dammy.dammy"
 D "Oracle Java Silver/0123.pdf"
 D "Oracle Java Silver/ClassObjectMethod/basic.md"
 D "Oracle Java Silver/LogicCalculation/basic.md"
 D "Oracle Java Silver/ObjectOrientation/AbstractClassBasic.md"
 D "Oracle Java Silver/ObjectOrientation/EncapsulationBasic.md"
 D "Oracle Java Silver/ObjectOrientation/InheriantanceBasic.md"
 D "Oracle Java Silver/ObjectOrientation/InterfaceBasic.md"
 D "Oracle Java Silver/ObjectOrientation/NewFeatureBasic.md"
 D "Oracle Java Silver/ObjectOrientation/Override&OverloadBasic"
 D "Oracle Java Silver/ObjectOrientation/PolymorphismBasic.md"
 D "Oracle Java Silver/ObjectOrientation/TypeCastBasic.md"
 D "Oracle Java Silver/dataType/basic.md"
 D "Oracle Java Silver/javaBasic/basic.md"
 M README.md
?? aws-saa/
?? log/
?? oracle-java-silver/
Exit code: 0
```

## 2026-07-07 21:38:03 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
git diff --check
```

Output:

```text
warning: in the working copy of 'README.md', LF will be replaced by CRLF the next time Git touches it
Exit code: 0
```

## 2026-07-07 21:38:03 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
git add -A
```

Output:

```text
warning: in the working copy of 'README.md', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'aws-saa/README.md', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'log/command-log.md', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'oracle-java-silver/README.md', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'oracle-java-silver/notes/fundamentals/01-java-basics.md', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'oracle-java-silver/notes/fundamentals/02-data-types.md', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'oracle-java-silver/notes/fundamentals/03-operators-and-flow.md', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'oracle-java-silver/notes/fundamentals/04-classes-objects-methods.md', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'oracle-java-silver/notes/java-17/12-java-17-features.md', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'oracle-java-silver/notes/object-oriented/05-encapsulation.md', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'oracle-java-silver/notes/object-oriented/06-inheritance.md', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'oracle-java-silver/notes/object-oriented/07-polymorphism.md', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'oracle-java-silver/notes/object-oriented/08-type-casting.md', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'oracle-java-silver/notes/object-oriented/09-abstract-classes.md', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'oracle-java-silver/notes/object-oriented/10-interfaces.md', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'oracle-java-silver/notes/object-oriented/11-overriding-overloading.md', LF will be replaced by CRLF the next time Git touches it
Exit code: 0
```

## 2026-07-07 21:38:03 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
git status --short
```

Output:

```text
D  "AWS SAA/dammy.dammy"
D  "Oracle Java Silver/ClassObjectMethod/basic.md"
D  "Oracle Java Silver/ObjectOrientation/EncapsulationBasic.md"
D  "Oracle Java Silver/ObjectOrientation/TypeCastBasic.md"
M  README.md
A  aws-saa/README.md
R  "AWS SAA/SAA-C03  \351\242\230\347\233\256\344\270\255\346\226\207\347\211\210.pdf" -> aws-saa/resources/saa-c03-questions-zh.pdf
AM log/command-log.md
A  oracle-java-silver/README.md
R  "Oracle Java Silver/javaBasic/basic.md" -> oracle-java-silver/notes/fundamentals/01-java-basics.md
R  "Oracle Java Silver/dataType/basic.md" -> oracle-java-silver/notes/fundamentals/02-data-types.md
R  "Oracle Java Silver/LogicCalculation/basic.md" -> oracle-java-silver/notes/fundamentals/03-operators-and-flow.md
A  oracle-java-silver/notes/fundamentals/04-classes-objects-methods.md
R  "Oracle Java Silver/ObjectOrientation/NewFeatureBasic.md" -> oracle-java-silver/notes/java-17/12-java-17-features.md
A  oracle-java-silver/notes/object-oriented/05-encapsulation.md
R  "Oracle Java Silver/ObjectOrientation/InheriantanceBasic.md" -> oracle-java-silver/notes/object-oriented/06-inheritance.md
R  "Oracle Java Silver/ObjectOrientation/PolymorphismBasic.md" -> oracle-java-silver/notes/object-oriented/07-polymorphism.md
A  oracle-java-silver/notes/object-oriented/08-type-casting.md
R  "Oracle Java Silver/ObjectOrientation/AbstractClassBasic.md" -> oracle-java-silver/notes/object-oriented/09-abstract-classes.md
R  "Oracle Java Silver/ObjectOrientation/InterfaceBasic.md" -> oracle-java-silver/notes/object-oriented/10-interfaces.md
R  "Oracle Java Silver/ObjectOrientation/Override&OverloadBasic" -> oracle-java-silver/notes/object-oriented/11-overriding-overloading.md
R  "Oracle Java Silver/0123.pdf" -> oracle-java-silver/resources/oracle-java-silver-reference.pdf
Exit code: 0
```

## 2026-07-07 21:38:03 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
git diff --cached --stat
```

Output:

```text
 AWS SAA/dammy.dammy                                |    0
 Oracle Java Silver/ClassObjectMethod/basic.md      |   41 -
 .../ObjectOrientation/EncapsulationBasic.md        |   43 -
 .../ObjectOrientation/TypeCastBasic.md             |    2 -
 README.md                                          |   15 +-
 aws-saa/README.md                                  |    7 +
 .../resources/saa-c03-questions-zh.pdf             |  Bin
 log/command-log.md                                 | 1755 ++++++++++++++++++++
 oracle-java-silver/README.md                       |   36 +
 .../notes/fundamentals/01-java-basics.md           |  295 ++--
 .../notes/fundamentals/02-data-types.md            |   36 +-
 .../notes/fundamentals/03-operators-and-flow.md    |   34 +-
 .../fundamentals/04-classes-objects-methods.md     |   90 +
 .../notes/java-17/12-java-17-features.md           |   58 +-
 .../notes/object-oriented/05-encapsulation.md      |   47 +
 .../notes/object-oriented/06-inheritance.md        |   35 +-
 .../notes/object-oriented/07-polymorphism.md       |   14 +-
 .../notes/object-oriented/08-type-casting.md       |   77 +
 .../notes/object-oriented/09-abstract-classes.md   |    8 +-
 .../notes/object-oriented/10-interfaces.md         |   83 +-
 .../object-oriented/11-overriding-overloading.md   |   26 +-
 .../resources/oracle-java-silver-reference.pdf     |  Bin
 22 files changed, 2367 insertions(+), 335 deletions(-)
Exit code: 0
```

## 2026-07-07 21:38:03 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
git add -A
```

Output:

```text
<no output; stages command-log entries before commit>
Exit code: 0
```

## 2026-07-07 21:38:03 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
git commit -m "Organize Java Silver study notes"
```

Output:

```text
<commit output is displayed by this terminal command after the log entry is staged>
Exit code: 0
```

## 2026-07-07 21:40:22 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
git branch --show-current
```

Output:

```text
write/silver
Exit code: 0
```

## 2026-07-07 21:40:22 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
git status --short --branch
```

Output:

```text
## write/silver...origin/write/silver [ahead 1]
 M log/command-log.md
Exit code: 0
```

## 2026-07-07 21:40:22 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
git log -1 --oneline
```

Output:

```text
477c122 Organize Java Silver study notes
Exit code: 0
```

## 2026-07-07 21:40:22 +09:00

Working directory: `C:\documents\project\java certification\oracle java se\Learn-Java-EE`

Command:

```powershell
git add -A
```

Output:

```text
<no output; stages command log entries before push>
Exit code: 0
```

