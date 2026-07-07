# Overriding and Overloading

## 重载调用的优先级

| 优先级 | 规则 | 示例 |
| --- | --- | --- |
| 1 | 完全一致 | `int` 匹配 `int` |
| 2 | 范围扩展 widening | `int` -> `long` |
| 3 | 装箱 boxing | `int` -> `Integer` |
| 4 | 可变参数 varargs | `int...` |

> 范围扩展优先于装箱，可变参数优先级最低。

## 关于null

### 匹配会优先到范围更小更具体的重载方法

如参数为null时 比起Object更优先调用参数类型为String的方法
*如果无法比较谁更加具体则会报错 比如Integer和String，因为两者不存在继承关系*

## static方法隐藏

> 子类定义了一个和父类 static 方法同名、同参数的方法时，它不是 override，而是把父类的 static 方法“隐藏”了。
因此按照引用类型的static方法进行执行

## 是重写还是重载
- 重载先在编译期决定
- 重写再在运行期决定

- 重载看引用类型 
- 重写看实际对象

## 和异常

- 重写时
    - 不能抛出更宽的 checked exception
    - 可以抛出更窄的 checked exception
    - 可以不抛出
    - RuntimeException 不受这个限制

## 重写规则

- 方法名和参数列表必须相同。
- 返回类型必须相同，或者是协变返回类型 covariant return type。
- 访问权限不能比父类方法更窄。
- `private`、`final`、`static` 方法不能被真正重写。
