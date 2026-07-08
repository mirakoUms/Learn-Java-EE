# 例外处理

## 概念

> Java 中能被 throw 抛出、能被 catch 捕获的对象，必须是 Throwable 或其子类。Throwable 是所有异常和错误的父类。

```bash
java.lang.Throwable
├── java.lang.Error
└── java.lang.Exception
    └── java.lang.RuntimeException
```

| 类型                                    | 日语      | 是否必须处理                    | 代表                     |
| ------------------------------------- | ------- | ------------------------- | ---------------------- |
| `Error`                               | エラー     | 不需要，也通常不处理                | `OutOfMemoryError`     |
| `RuntimeException` 及其子类               | 非チェック例外 | 不强制处理                     | `NullPointerException` |
| `Exception` 但不是 `RuntimeException` 子类 | チェック例外  | 必须 `try-catch` 或 `throws` | `IOException`          |


## Throwable提供的方法

- getMessage() 取得异常对象里的详细消息。

- printStackTrace() 打印异常发生的位置，也就是堆栈信息。

- getCause() 取得异常原因



## Compile例外检查

> 只要代码中可能抛出 checked exception，就必须进行处理

> The class Exception and any subclasses that are not also subclasses of RuntimeException are checked exceptions. Checked exceptions need to be declared in a method or constructor's throws clause if they can be thrown by the execution of the method or constructor and propagate outside the method or constructor boundary.

### 处理方法

- try catch

- 方法或者构造器的后面加 throws Exception

## 非例外检查

> RuntimeException 及其子类是 unchecked exception，不需要强制 try-catch 或 throws。

- 运行时例外， 表示通过编译 但运行中出现的例外 常见：
    - NullPointerException
        ```Java
        String a = null;
        a.toString();
        ```
    - ArithmeticException
        ```Java
        int a = 10 / 0;
        ```
    - ArrayIndexOutOfBoundsException
        ```Java
        String a[] = new String[2];
        a[10] = "test";
        ```
    - StringIndexOutOfBoundsException
        ```Java
        String a = "www";
        System.out.println(a.charAt(10));
        ```
    - ClassCastException
    - NumberFormatException
    - IllegalArgumentException

## Error

- 表示JVM层面的问题 是Throwable的子类

- 常见
    - OutOfMemoryError
    - StackOverflowError
    - ExceptionInInitializerError

- 一般不需要进行处理


## try catch 代码块

### 基本语法

```Java
try {
    // 可能发生例外的代码
} catch (ExceptionType e) {
    // 处理例外
}
```

- 注意try{}内在发生例外的位置向下不会执行:

```Java
try {
    System.out.println("1");
    String a = null;
    String b = a.toString();
    System.out.println("12"); // 不会打印输出
} catch (NullPointerException e) {
    System.out.println("123");
}
```

### 多个catch时的匹配顺序

> 多个 catch 时，必须 子类在前，父类在后。

```Java
catch (Exception e) {
    System.out.println("runtime");
} catch (RuntimeException e) { // Compile Error: Unreachable catch block for RuntimeException. It is already handled by the catch block for Exception
    System.out.println("exception");
}
```

### 合法的try catch 

- 必须包含以下
    - try
    - 大于等于一个catch或者finally

### finally 与 return 

```Java
static int test() {

    //返回2 finally会覆盖try的return
    try {
        return 1;
    } finally {
        return 2;
    }
}
```
## throw 与 throws

- throw：手动抛出异常 后面必须是Throwable或其子类的实例对象

```Java
throw new Exception(); // 合法 但必须进行处理 
throw new RuntimeException();
throw new Error();
```

- throws: 声明一个方法或构造器可能抛出某异常

## 自定义例外

- 可以选择继承Checked Exception或者unchecked Exception


## multi-catch

> java7加入 类似fallthrough 可以让多个异常公用一个处理逻辑

- 异常间不可以有继承关系

```Java
try {
    // Compile Error: The exception NullPointerException is already caught by the alternative RuntimeException
} catch (RuntimeException | NullPointerException e) {
}
```

- 捕捉到的例外变量为隐式final

```Java
try {
    // code
} catch (ArithmeticException | NullPointerException e) {
    e = new RuntimeException(); // Compile Error: The parameter e of a multi-catch block cannot be assigned
}
```

## try with resource

> Resource: 用完必须关闭的资源

- 文件
- 数据库连接
- 网络连接
- 输入输出流
- Scanner

不关闭会占用资源

### 基本用法

```Java
try (FileReader fr = new FileReader("data.txt")) {
    // 读取文件
} catch (IOException e) {
    System.out.println("发生异常");
}
```

- Java 会在 try 块结束后，自动执行：close 不需要手动写final

- 资源类必须实现closeable 或者autocloseable

### 资源关闭时机

- 多个资源 先关闭后面

```Java
try (R r1 = new R("1"); R r2 = new R("2")) {
}
```

## 与类的继承组合出题

> 只对checked Exception：子类重写方法不能比父类方法抛出更宽泛的 checked exception。可以抛出一样，更具体的例外 也可以不抛出例外

```Java
class AA {
   public void func() throws IOException {
      System.out.println("a");
   }
}
class BB extends AA {
   public void func() throws Exception { // Exception Exception is not compatible with throws clause in AA.func()
      System.out.println("a"); 
   }
}
```

> unchecked Exception不受此约束

```Java
class AA {
   public void func() throws ArrayIndexOutOfBoundsException {
      System.out.println("a");
   }
}

class BB extends AA {
   public void func() throws RuntimeException { // 正常编译
      System.out.println("a"); 
   }
}
```