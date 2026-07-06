### Wrapper Class ラッパクラス
- byte -> Byte
- int -> Integer
- *char -> Character*
- *short -> Short*
- ....


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
```Java
String name = null;
Optional<String> name = Optional.of(name); //　nullpointerException
```

### Fall Through

> Java 17 的 -> 写法不会 fall through

```Java
// Java 17 新功能

int x = 1;

switch (x) {
    case 1 -> System.out.println("A");
    case 2 -> System.out.println("B");
    case 3 -> System.out.println("C");
}// 输出：A
```

### final

```java
final int a; // correct: not nesssarily assign value to it when assert final 
a = 10; // first time: correct
a = 20; // second time: error

final void foo();
@override
final void foo(); // error: final method cannot be overide

final Class foo() {

}

final Class foo2 extends foo() {
    // error: final Class cant not be extended
}

## 不可变类


## record
