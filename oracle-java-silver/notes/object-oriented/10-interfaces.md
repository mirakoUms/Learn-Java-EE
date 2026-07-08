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

- 抽象类实现接口时 可以选择性实现抽象方法

 ```Java
 public interface Test {
    void func();
 }

 abstract class A implements Test {
    public abstract void func(); // 声明抽象方法
 }

 abstract class B implements Test {
    public void test() {} // 不实现func 因为编译器认为可以留给B的实现类去实现
 }
 ```

## 变量

> 接口中的字段隐式是 public static final，并且接口字段必须有初始化值。

如: 

```java
interface Flyable {
    public static final float FLY_SPEED = 27.3f;
    // 等价于 float FLY_SPEED = 27.3f
    // class body
}
```

## 接口方法

- 以下四种定义实质一样

```Java
public abstract void func();
abstract void func();
public void func();
void func();
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


## 函数式接口

### 有且只有一个接口抽象方法
```Java 
interface I {
    void func();

    // 可以加static， default， private方法
}
```

### 可以使用@FucntionalInterface注解进行检查

```Java
@FunctionalInterface
interface I {
    void func();
    void func2();// Error I 不是函数式接口
}
```

表示这是一个函数式接口，如果不满足函数式接口的定义则编译错误

### 用法 常结合lambda式使用

```Java
interface I {
    void func();
}

I i = () -> System.out.println("functional interface");
i.func(); // functioal interface;
```

### Predicate 条件判断器

> Predicate 是 Java 8 引入的一个函数式接口

```Java
java.util.function.Predicate<T>
```

#### 作用 

接收一个参数，返回 boolean

#### 核心用法

```Java
boolean test(T t);
```

```Java
Predicate<String> p = s -> s.length() > 3;

System.out.println(p.test("Java")); // true
System.out.println(p.test("Hi"));   // false
```

#### 常用于Stream.filter等 限制条件

例1：

```java
List<String> list = new ArrayList<>(); 

list.add("a");
list.add("aaqaa");
list.add("b");


list.stream()
    .filter(s -> s.length() > 3)
    .forEach(System.out::println);
```

例2：

```java
List<String> list = new ArrayList<>(); 

list.add("a");
list.add("aaqaa");
list.add("b");


list.removeIf(s -> s.length() > 3);
for(String s : list) {
    System.out.println(s);
}
```

#### 对比
Predicate<T>      T -> boolean
Consumer<T>       T -> void
Function<T, R>    T -> R
Supplier<T>       () -> T