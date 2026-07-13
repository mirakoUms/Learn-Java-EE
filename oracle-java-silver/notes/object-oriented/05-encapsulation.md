# Encapsulation 封装

## 作用

- 隐藏内部成员变量

- 自定义逻辑控制成员变量的值

## 可见性

| 修饰符 | 同类 | 同包 | 不同包子类 | 不同包非子类 |
| --- | --- | --- | --- | --- |
| `private` | yes | no | no | no |
| package-private | yes | yes | no | no |
| `protected` | yes | yes | yes* | no |
| `public` | yes | yes | yes | yes |

> 不写修饰符不等于 `public`，而是 package-private。

```java
private String gender;

public void setGender(String gender) {
    if (!"male".equals(gender) && !"female".equals(gender)) {
        // 对非法值进行控制
        return;
    }
    this.gender = gender;
}
```

## Protected的访问范围

- *在不同包的子类中：不可以通过父类实例访问protected字段*

- 但是可以使用子类实例访问

## 构造器的访问权限

- 仍遵循以上原则

    - 如果构造器为 `private`，那么将无法在类外使用这个构造器

    - 包外部使用构造器时需要是 `public`，否则不可见

## 方法重写时

- 可以保持不变或者范围扩大 “无法从public到private”

- private 方法不能被重写
