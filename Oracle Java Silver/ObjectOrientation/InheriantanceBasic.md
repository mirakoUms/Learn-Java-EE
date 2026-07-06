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

```Java
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

```Java
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
```Java
class Room {
    static {
        System.out.println("Static init");
    }
}
```
> init
```Java
class Room {
    {
        System.out.println("Static init");
    }
}
```

- 父类static -> 子类static -> 父类init -> 父类constructor -> 子类init -> 子类constructor 
- static代码块在一次执行者仅执行一次