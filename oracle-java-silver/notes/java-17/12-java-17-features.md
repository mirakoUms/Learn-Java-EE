# Java 17 Features

## sealed Java17

> sealed class / sealed interface 用来限制哪些类或接口可以继承或实现它。

### 基本写法

```java
sealed class Animal permits Dog, Cat {
    // 只允许被Dog，Cat继承
}

final class Dog extends Animal {
}

final class Cat extends Animal {
}
```

### permitted 子类的规则

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


### 继承限制

> record class 隐式继承 `java.lang.Record`，并且隐式是 `final`。因此 record 不能继承其他类，也不能被继承。

```java
sealed class Animal permits Dog { }
record Dog(String name) extends Animal { } // Error: record 不能 extends 其他类
```

### 实现接口

> record 不能继承别的类，因为它已经隐式继承 java.lang.Record，但可以实现一个或多个接口。

```java
record Bird(String name, String species) implements Flyable { }
```

### 字段限制

> record不能声明额外的 instance variables，也不能有 instance initializer；但可以声明 static 字段和 static 方法。

```java
record User(String name) {
    static int count;
    // int age; // Error
}
```

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
record Bird(String name) implements Flyable { } // record 隐式 final，适合作为 sealed 类型的 permitted subclass。
```
