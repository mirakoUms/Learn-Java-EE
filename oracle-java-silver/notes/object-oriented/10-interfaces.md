# interface 接口

## 定义

```java
interface Flyable {
    void fly(); // 等同于 public abstract void fly();
    // 实现时不能省略 public，不写会变成 package-private
}
```

## 不能直接实例化 但是可以声明指向子类的引用型

```java
// Flyable f = new Flyable(); // Error
Flyable f = new Bird(); // Bird 实现 Flyable
```

## 规则

- 必须先继承 后实现

```java
class Bird extends Animal implements Flyable {
    // class body
}
```

- 可以实现多个接口

```java
class Bird implements Flyable, LayEggable {
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

```java
interface Tool {
    static void reset() {
    }
}

Tool.reset();
// new ToolImpl().reset(); // Error
```

> 接口的 static 方法不会被实现类继承，因此多个接口存在同名 static 方法时不会产生重写冲突。

## default 方法冲突

实现多个接口时，如果多个接口提供相同签名的 `default` 方法，实现类必须自己重写并消除冲突。

```java
interface A {
    default void test() {
    }
}

interface B {
    default void test() {
    }
}

class C implements A, B {
    public void test() {
        A.super.test();
    }
}
```

## private方法 

- 不能被实现类实现 用于default或者static方法共同部分的包装

## 父类的方法优先于接口的方法

> 继承体系独立性

## 接口的继承

- 接口可以继承 实现类则必须实现接口父类以及接口类中全部的抽象方法

- 接口可以继承自多个接口 相较于类只能继承一个类
