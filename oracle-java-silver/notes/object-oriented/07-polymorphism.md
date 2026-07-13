# Polymorphism 多态

简单来讲父类变量可以指向子类实例，同时使用重写方法等

> 编译时看引用类型 运行时看实际类型

```java
Parent p = new Child();
```

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

System.out.println(a.name); // 字段没有多态，编译时看引用类型，因此输出 animal
a.print();                  // Dog重写了Animal的print方法，看实际类型输出 Dog method
```

> 成员变量不参与多态

```Java
class Parent {
    String name = "p";
    static String staticName = "staticP";
}

class Child extends Parent {
    String name = "c";
    static String staticName = "staticC";
}

public class Test {
    public static void main(String[] args) {
        Parent p = new Child(); // p
        System.out.println(p.name); // staticP
    }
}
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


