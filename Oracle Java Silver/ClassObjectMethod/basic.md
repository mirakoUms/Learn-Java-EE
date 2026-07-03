
## constructor

### 默认构造器 

> 如果类中没有写任何构造器，编译器会自动生成一个无参构造器。
> 只要写了任意构造器，默认构造器就不会生成


### 重构构造器

### this()/super()

- `this()` 用来在 同一个类内部复用构造器逻辑。

```Java
class User {
    String name;
    int age;

    User() {
        this("unknown", 0);
    }

    User(String name) {
        this(name, 0);
    }

    User(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

- super() 用来调用 父类构造器




### 初始化顺序