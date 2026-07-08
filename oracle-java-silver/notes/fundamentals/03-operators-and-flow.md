# Operators and Flow

运算符与控制结构。

## 逻辑
### 可以进行逻辑运算与位运算
- ^ 异或 排他逻辑或
- & 按位与
- | 按位或
- ~ 按位取反 计算公式`~x == -x - 1`

> &和|的逻辑运算不会短路

### 移位运算
- basic
```java
System.out.println(6 << 2);// 0110 -> 0001 1000 24
System.out.println(-6 >> 2);// -1000 -> -0010 -2
// 无符号右移，英文叫 unsigned right shift。
System.out.println(-6 >>> 2);
// 11111111 11111111 11111111 11111010 -> 00111111 11111111 11111111 11111110
```
- long 实际移动位数 = n % 64
```java
System.out.println(1L << 64); // 1
System.out.println(1L << 65); // 2
```
### instanceof

> 用来判断对象是不是某个类的实例

- 基本用法 `obj instanceof Type` 返回 boolean

- null instanceof 返回false -> null 不是任何类的实例

- obj必须是引用类型，不能是基本类型

```java
Object value = "Java";

if (value instanceof String text) {
    System.out.println(text.length());
}
```


## Switch

### 支持的数据类型

- `byte`、`short`、`char`、`int` 以及对应包装类
- String
- 枚举 enum

> 不支持 `long`、`float`、`double`、`boolean`。

### java 17 新语法

- 不会fall through， 但可以多个情况放在一起处理
```java
int x = switch (1) {
    case 1, 2, 3 -> 1;
    case 4, 5 -> 2;
    default -> 3;
};
```
- 当 case 里面不是简单一行，而是有多行处理逻辑时，需要用 yield 返回结果。

```Java
int num = 1;

String result = switch (num) {
    case 1 -> {
        System.out.println("处理 case 1");
        yield "one";
    }
    case 2 -> {
        System.out.println("处理 case 2");
        yield "two";
    }
    default -> {
        yield "other";
    }
};

System.out.println(result);
```