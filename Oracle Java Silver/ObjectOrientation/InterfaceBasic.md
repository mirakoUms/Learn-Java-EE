# interface 接口

## 定义

 ```Java
 interface Flyable {
    void fly(); // 等同于 public abstract void fly();
    // 进行实现时不能省略public(不写默认范围为package private) 
 }
 ```

 ## 不能直接实例化 但是可以声明指向子类的引用型
 ```Java
 // Flyable f = new Flyable(); // Error
Flyable f = new Bird(); // bird实现flyable
 ```

## 规则

- 必须先继承 后实现
 ```Java
public Bird extends Animal implements Flyable {
    // class body
}
 ```

- 可以实现多个接口
 ```Java
public Birds implements Flyable, Layeggable {
    // class body
}
 ```

 ## 变量

 > 接口中的字段隐式是 public static final，并且接口字段必须有初始化值。

并且命名习惯大写 加 下划线分割符 如 
```Java
interface Flyable {
    public static final float FLY_SPEED = 27.3f;
    // class body
}
 ```


## default 方法

> default 方法可以给接口增加新功能，同时保持和旧实现类的兼容性。

```Java
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