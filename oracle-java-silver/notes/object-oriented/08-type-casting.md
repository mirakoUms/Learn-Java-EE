# Type Casting 类型转换

## 基本类型转换

### 自动类型提升 widening

范围小的类型可以自动转换为范围大的类型。

```java
int i = 10;
long l = i;      // int -> long
double d = l;    // long -> double
```

常见顺序：

```text
byte -> short -> int -> long -> float -> double
char -> int
```

> `byte`、`short`、`char` 参与算术运算时通常会先提升为 `int`。

```java
byte a = 1;
byte b = 2;
// byte c = a + b; // Error: a + b 的结果是 int
int c = a + b;
```

### 强制类型转换 narrowing

范围大的类型转换为范围小的类型时需要显式强制转换，可能丢失精度或溢出。

```java
double d = 10.8;
int i = (int) d; // 10

int value = 130;
byte b = (byte) value; // 溢出
```

## 引用类型转换

### 向上转型 upcasting

子类对象可以自动转成父类引用。

```java
Dog dog = new Dog();
Animal animal = dog;
```

### 向下转型 downcasting

父类引用转回子类引用需要显式强制转换。编译可能通过，但运行时对象类型不匹配会抛出 `ClassCastException`。

```java
Animal animal = new Dog();
Dog dog = (Dog) animal; // OK

Animal other = new Cat();
// Dog wrong = (Dog) other; // ClassCastException
```

## instanceof

向下转型前先用 `instanceof` 判断，可以避免运行时异常。

```java
Animal animal = new Dog();

if (animal instanceof Dog dog) {
    dog.bark();
}
```

