# Classes, Objects, and Methods

## Class and Object

- class 是对象的模板。

- object 是 class 实例化后的具体对象。

- 成员变量定义在类中、方法外；局部变量定义在方法或代码块中。

```java
class User {
    String name; // instance variable

    void greet() {
        String message = "hello"; // local variable
        System.out.println(message + ", " + name);
    }
}
```

## Constructor

### 默认构造器 

> 如果类中没有写任何构造器，编译器会自动生成一个无参构造器。
> 只要写了任意构造器，默认构造器就不会生成


### 重载构造器

### this()/super()

- `this()` 用来在同一个类内部复用构造器逻辑。

- `super()` 用来调用父类构造器。

- `this()` 和 `super()` 都必须是构造器中的第一条语句，因此不能同时出现在同一个构造器里。

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

```java
class Animal {
    Animal(String name) {
    }
}

class Dog extends Animal {
    Dog() {
        super("dog");
    }
}
```

## Method

- 方法签名 method signature 由方法名和参数列表组成，不包含返回值。

- 同一个类中可以重载方法；重载方法必须参数列表不同。

- 方法参数是局部变量，方法结束后生命周期结束。

```java
void print(int value) {
}

void print(String value) {
}
```

### 初始化顺序

1. 父类 static 字段和 static 初始化块。

2. 子类 static 字段和 static 初始化块。

3. 父类实例字段和实例初始化块。

4. 父类构造器。

5. 子类实例字段和实例初始化块。

6. 子类构造器。
