# Polymorphism 多态

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


