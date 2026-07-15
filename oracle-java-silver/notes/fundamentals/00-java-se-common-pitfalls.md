# Java SE Common Pitfalls

Java の概要、実行可能な Java プログラム、コンパイルと実行、package/import の易错点总结。

## main メソッド

### 标准入口

JVM 查找的是下面这种入口方法。

```java
public static void main(String[] args) {
}
```

易错点：

- `public` 不能省略，否则 JVM 无法从类外调用。

- `static` 不能省略，否则 JVM 不能不创建对象就调用。

- 返回值必须是 `void`。

- 方法名必须小写 `main`。

- 参数可以是 `String[] args` 或 `String... args`。

- `args` 只是变量名，可以改名。

```java
public static void main(String... values) {
    System.out.println(values.length);
}
```

### main 可以重载

可以写多个 `main`，但 JVM 只把标准签名当入口。

```java
public class MainSample {
    public static void main(String[] args) {
        System.out.println("entry point");
    }

    public static void main(int value) {
        System.out.println("overload");
    }
}
```

## public class 和文件名

### public class 必须匹配文件名

```text
Hello.java
```

```java
public class Hello {
}
```

易错点：

- 一个 `.java` 文件中最多只能有一个 `public` 顶级类。

- 如果有 `public class Hello`，文件名必须是 `Hello.java`。

- 没有 `public` 顶级类时，文件名不一定要和类名一致。

- Java 区分大小写，`Hello.java` 和 `hello.java` 不是同一个名字。

## コンパイルと実行

### 没有 package

```powershell
javac Hello.java
java Hello
```

易错点：

- `javac` 编译源文件时写 `.java`。

- `java` 执行 class 时不写 `.class`。

- `java Hello.class` 是错误写法。

- 当前目录需要能找到编译后的 `Hello.class`。

## package 宣言

为了分层级对class文件进行管理

### package 的位置

```java
package com.example.app;

public class Main {
}
```

易错点：

- `package` 必须是第一条非注释语句。

- 一个源文件最多只能有一个 `package` 声明。

- package 名通常全小写。

- package 名应该和目录结构对应。

- default package 中的类不能被其他 package 的类 import。

### 有 package 时的编译和执行

```text
src/
  com/
    example/
      app/
        Main.java
```

```powershell
javac -d out src/com/example/app/Main.java
java -cp out com.example.app.Main
```

易错点：

- 有 package 时，执行要写 fully qualified class name。

- `java Main` 找不到 `com.example.app.Main`。

- `javac -d out` 会按 package 生成目录。

- `-cp out` 告诉 JVM 从 `out` 目录开始找 class。

## import

### package / import / class 的顺序

```java
package com.example.app;

import java.util.ArrayList;
import java.util.List;

public class Main {
}
```

易错点：

- 顺序必须是 `package` -> `import` -> `class`。

- `import` 只能写在 class 声明之前。

- `java.lang` 自动导入，例如 `String`、`System`。

- 同一个 package 中的类不需要 import。

- `import java.util.*;` 不会导入 `java.util.concurrent`。

- wildcard import 不会导入子 package。

```java
import java.util.*;            // List, ArrayList
import java.util.concurrent.*; // 子 package 需要单独 import
```

### 同名类冲突

如果两个 package 中有同名类，不能同时用普通 import 简化成同一个简单类名。

```java
import java.sql.Date;
// import java.util.Date; // 和 java.sql.Date 简名冲突

class Sample {
    Date sqlDate;
    java.util.Date utilDate;
}
```

## 命令行参数

```powershell
java Main one two
```

```java
public class Main {
    public static void main(String[] args) {
        System.out.println(args.length); // 2
        System.out.println(args[0]);     // one
    }
}
```

易错点：

- 命令行参数从 `args[0]` 开始。

- 参数之间用空格分隔。

- 没有参数时 `args.length == 0`，不是 `args == null`。