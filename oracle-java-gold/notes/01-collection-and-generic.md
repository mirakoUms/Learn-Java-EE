# 集合

用于保存和操作(CRUD，搜索，自定义规则。。。)一组对象

## 大体框架

```bash
Iterable<E>
    └── Collection<E>
          ├── List<E>
          ├── Set<E>
          │     └── SortedSet<E>
          │            └── NavigableSet<E>
          └── Queue<E>
                └── Deque<E>
```

- 键值对Map<K, V> 不属于 Collection

## 常见实现类

```bash
List
 ├── ArrayList
 └── LinkedList 

Set
 ├── HashSet
 ├── LinkedHashSet
 └── TreeSet

Queue / Deque
 ├── ArrayDeque
 ├── LinkedList
 └── PriorityQueue（只实现 Queue）

Map
 ├── HashMap
 ├── LinkedHashMap
 └── TreeMap
```


# 泛型

限制集合中可以保存数据的类型 例如String，Integer或者自定义类等

## 泛型类

```java
class Box<T> {
    private T value; // 尖括号里的 T 是类型参数，可以替换为任意引用类型。

    public void set(T value) {
        this.value = value;
    }

    public T get() {
        return value;
    }
}
```

- 常见类型参数命名 （命名规范相关）

    - T	Type

    - E	Element

    - K	Key

    - V	Value

    - R	Result

    - N	Number

## 菱形运算符

Java可以根据左侧推测类型，因此右侧可以不写数据类型

```java
List<String> a = new ArrayList<String>();
List<String> b = new ArrayList<>(); // Correct
```

但是与var的使用需要注意

```java
var<String> a = new ArrayList<>();// Compile Error: 'var' cannot be used with type arguments
var a = new ArrayList<>(); // Correct 这里右侧会被认为是Object的ArrayList
```

## 泛型只能使用封装类

```java
List<int> a = new ArrayList<>(); // Compile Error: Syntax error, insert "Dimensions" to complete ReferenceType
List<Integer> b = new ArrayList<>();

b.add(10); // 会自动boxing，相当于b.add(Integer.ValueOf(10))
int n = b.get(0) // 自动unboxing，相当于int n = ((Integer) b.get(0)).inValue();
```

## 泛型方法

```java
public static void main(String[] args) {
    System.out.println(geta(List.of("Cat", "Dog"))); // Cat
    System.out.println(geta(List.of(1, 2))); // 1
    // 显式指定类型
    System.out.println(Test.<Integer>geta(List.of(1, 2))); // 1
}

// <T> T 替换普通方法的返回值类型
public static <T> geta(List<T> list) {
    return list.get(0); 
}
```

## 上界

泛型上界用于规定：类型参数 T 最多只能是某个类型及其子类型。

```java
public static <T extends Number> T geta(List<T> list) { } // 规定T必须是Number或者其子类（如Integer，Double等）
```

- T 参数类型

- extends 限制上界

- Number 上界类型

### 作用


用于限制类型参数的范围

```java
public static <T> Double getDouble(T t) {
    return t.doubleValue(); // Compile Error: The method longValue() is undefined for the type T
}

public static <T extends Number> Long getLong(T t) {
    return t.longValue();  // 正常编译
}

public static <T extends Double> Double getDouble(T t) { // 这里一般不推荐继承一个final类 但不会报错
    return t.doubleValue(); 
}
```

### 泛型类的上界

```java
class Box<T extends Number> { // 限制参数类型只能是Number或其子类
    T val;

    void print() {
        System.out.println(val.doubleValue()); // 可以使用Number的抽象方法
    }
}
```

```java
Box<String> box1 = new Box<>(); // Compile Error: Bound mismatch
Box<Integer> box2 = new Box<>(); // Correct: 因为Intger是Number的实现类
```

### 接口的实现

