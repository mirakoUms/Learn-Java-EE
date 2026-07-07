# 抽象类

## 抽象类也有自己的构造方法

- 但是自己无法实例化 所以构造方法给子类用
- 抽象类可以有抽象方法，也可以有普通方法。
- 如果一个类包含抽象方法，这个类必须声明为 `abstract`。
- 子类必须实现所有抽象方法，除非子类本身也是抽象类。

## 抽象类不能使用以下关键字进行声明

- final

abstract抽象需要进行重写，因此需要被继承，不可以用final同时修饰

## 抽象方法不能使用以下关键字声明

> It is a compile-time error if a method declaration that contains the keyword abstract also contains any one of the keywords private, static, final, native, strictfp, or synchronized.

```java
abstract static void test();   // 错
abstract final void test();    // 错
private abstract void test();  // 错
```

## 为什么与接口那么像

| 比较    | 抽象类              | 接口                          |
| ----- | ---------------- | --------------------------- |
| 关键字   | `abstract class` | `interface`                 |
| 继承/实现 | `extends`        | `implements`                |
| 数量    | 一个类只能继承一个父类      | 一个类可以实现多个接口                 |
| 实例变量  | 可以有普通实例变量        | 字段默认是 `public static final` |
| 构造方法  | 可以有              | 没有构造方法                      |
| 方法实现  | 可以有普通方法          | 可以有 `default`、`static`、`private` 方法 |
| 适合表达  | “是什么”            | “能做什么”                      |

> 抽象类定义对象是什么 接口则描述对象有哪些能力


