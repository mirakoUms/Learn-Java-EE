# Java Basics

### Wrapper Class ラッパクラス

| primitive | wrapper |
| --- | --- |
| `byte` | `Byte` |
| `short` | `Short` |
| `int` | `Integer` |
| `long` | `Long` |
| `float` | `Float` |
| `double` | `Double` |
| `char` | `Character` |
| `boolean` | `Boolean` |

> 自动装箱 autoboxing: `int` -> `Integer`。自动拆箱 unboxing: `Integer` -> `int`。


### Serialization　シリアライゼーション

> 将对象序列化，用于数据传输

- `static`, `transient` 不会被序列化
```java
class User implements Serializable {
    static String school = "ABC"; //static 属于类，不属于对象本身，所以不会作为对象状态被保存。
    String name;
    transient String password;
}
```

- serialVersionUID

用来判断“保存时的类”和“读取时的类”版本是否兼容。反序列化时会用它验证发送方和接收方加载的类是否兼容；如果不兼容抛出 `InvalidClassException`。

```java

private static final long serialVersionUID = 1L;
```


### Optional

> first appear: Java 8

#### 创建 Optional
- 有值：Optional.of()

```java
Optional<String> opt = Optional.of("Java");
```

- 可能为 null：Optional.ofNullable()

```java
String name = null;
Optional<String> opt = Optional.ofNullable(name);
```

> 如果 name 是 null，就得到一个空的 Optional。

- 空 Optional：Optional.empty()

```java
Optional<String> opt = Optional.empty();
```

- 如果optional.of()传null的参数则空指针异常
```java
String name = null;
Optional<String> opt = Optional.of(name); // NullPointerException
```

### Fall Through

> Java 17 的 -> 写法不会 fall through

```java
// Java 17 新功能

int x = 1;

switch (x) {
    case 1 -> System.out.println("A");
    case 2 -> System.out.println("B");
    case 3 -> System.out.println("C");
}// 输出：A
```

### final

- `final` 变量只能赋值一次。
- `final` 方法不能被重写。
- `final` 类不能被继承。

```java
final int value;
value = 10;
// value = 20; // Error: final variable cannot be assigned again

class Parent {
    final void foo() {
    }
}

class Child extends Parent {
    // void foo() {} // Error: final method cannot be overridden
}

final class Utility {
}

// class MoreUtility extends Utility {} // Error: final class cannot be extended
```

### intern

> Java 为了节省内存，相同的字符串字面量只保存一份
```java
String a = "Java";
String b = "Java";
```
          String Pool
      +-------------+
      |   "Java"    |
      +-------------+
          ▲      ▲
          │      │
          a      b

所以 a == b

> new String 
```java
String a = new String("Java");
```
            Heap
         +-----------+
    a -> | "Java"    |
         +-----------+

          String Pool
         +-----------+
         | "Java"    |
         +-----------+

> intern()
```java
String a = new String("Java");
String b = a.intern();
```
- 去 String Pool 找有没有内容相同的字符串。
    - 有 -> 返回 Pool 中那个对象。
    - 没有 -> 把当前字符串加入 Pool，再返回 Pool 中的对象。
