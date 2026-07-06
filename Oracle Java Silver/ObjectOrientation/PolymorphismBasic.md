# 父类引用 指向子类对象

> 编译时看引用类型 运行时看实际类型

> Parent p = new child();

## 适用范围

> 实例方法的重写

```Java
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

```Java
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


