# Inheritance 继承

> 继承允许子类继承父类的属性和方法，建立 is-a 关系。

## 只允许单类继承

```java
class Dog extends Animal, Mammal {} // Error: Java class 只允许单继承
```

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

    Parent() {
        System.out.println("Parent constructor");
    }

    void print() {
        System.out.println("Parent method");
    }
}

class Child extends Parent {
    String name = "Child";

    Child() {
        super(); // 调用父类无参构造器，必须是构造器第一条语句
    }

    void test() {
        super.print(); // 调用父类成员方法，但是无法访问 private 方法
        System.out.println(name);
        System.out.println(super.name);
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

```java
Parent p = new Child(); // Correct
p.cry();                // Error: 编译时只看 Parent 类型中有没有 cry()
```


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
        System.out.println("Instance init");
    }
}
```

- 父类static -> 子类static -> 父类init -> 父类constructor -> 子类init -> 子类constructor 
- static代码块在类第一次被使用时执行一次


## 实例方法的隐藏与重写

- 可以通过static隐藏方法，但是不能隐藏实例方法
```Java
class Parent {
    void func() {}
}

class Child {
    static void func() {} // Compile Error: This static method cannot hide the instance method from Parent
}
```

- 反过来不可以定义父类已经存在的static为实例方法

```Java
class Parent {
    static void func() {}
}

class Child {
    void func() {} // Compile Error: This instance method cannot override the static method from Parent
}
```