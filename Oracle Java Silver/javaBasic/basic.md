## 变量 variable

### 作用域

| 类型                     | 位置              | 有没有默认值    |
| ---------------------- | --------------- | --------- |
| 实例变量 instance variable | 类中，方法外，非 static | 有默认值      |
| 静态变量 static variable   | 类中，方法外，static   | 有默认值      |

| 局部变量 local variable    | 方法内部            | **没有默认值** |

```java
class Test {
    int a;          // 实例变量，默认值 0
    static int b;   // static变量，默认值 0

    public static void main(String[] args) {
        int c;      // 局部变量，没有默认值
        System.out.println(c); // 编译错误
    }
}
```