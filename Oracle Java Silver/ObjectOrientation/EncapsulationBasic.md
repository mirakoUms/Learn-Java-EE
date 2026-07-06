Encapsulation 封装

## 可见性

- *private 字段只能在 Person 类内部访问。其他类（即使是子类）中即使创建对象也无法访问*
- 不加修饰符不等于public 在其他包的类中无法访问 (package private)
- protected 在其他包的子类中有条件的访问 非子类无法访问
- public 完全开放

## getter setter 

### getter暴露私有成员变量 

### setter控制实例化的成员变量值
```Java
private String gender;

public void setGender(String gender) {
    if ("male".equals(gender) && "male".equals(gender)) {
        // 对不法值进行控制
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
    - 如果构造器为privtae，那么将无法在类外使用这个构造器
    - 包外部使用构造器时 需要是public否则不可见

## 方法重写时

- 可以保持不变或者范围扩大 “无法从public到private”
- private 方法不能被重写