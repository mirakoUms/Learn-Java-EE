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

## Collection

### 泛用方法

Collection实现了Iterable 继承Collection的子类可以使用其下的各种方法：

> 布尔值表示是否影响了原来的Collection对象

- boolean add(E e)

- boolean addAll(Collection<> c)

- boolean remove(Object o)

- boolean removeAll(Collection<?> c)

    - 去除Collection中存在于参数c中的对象

- boolean removeIf(Predicate<? super E> filter)

    - 可以写条件表达式 如去除所有偶数（n -> n % 2 == 0）

- boolean retainAll(Collection<?> c)

    - 只保留Collection中存在于参数c中的对象

- boolean contains(Object o)

- boolean containsAll(Collection<?> c)

- int size()

- boolean isEmpty()

- void clear()

- Iterator<E> iterator()

- Object[] toArray()

- <T> T[] toArray(T[] array)

### Iterate

#### Enhanced FOR 

> 本质仍是Iterator

```java
for (Object o: objectList) {
    // 
}
```

#### Iterator

```java
List<String> names = Arrays.asList("asd", "ad", "aca");

Iterator<String> iterator = names.iterator();

while (iterator.hasNext()) {
    String name = iterator.next();
    System.out.println(name);
}
```

遍历时删除元素

- 使用removeIf方法

List.removeIf(s -> s.equals("x"));

- 使用iterator

```java
List<String> lst = new ArrayList<>(List.of("a", "aa", "aaa"));

Iterator<String> iterator = lst.iterator();

while (iterator.hasNext()) {
    // 注意要加.next()
    if (iterator.next().equals("aa")) {
        iterator.remove();
    }
}

System.out.println(lst);
```

## List

有顺序 有索引 可重复 允许null

### 声明

> 声明原则 推荐变量声明使用接口类型，创建对象使用具体实现类。

```java
// 接口 变量 —— 具体实现类
List<String> list = new ArrayList<>();
```

### 特有方法

- void add(int index, E element)

- E get(int index)

- E set(int index, E element)

- E remove(int index)

    - 重载了boolean remove(Object object)

    - 注意使用区分

- int indexOf(Object o)

- int lastIndexOf(Object o)

- List<E> subList(int fromIndex, int toIndex)

    - 是视图，对子列表更改会影响到原来的列表。

    ```java
    List<String> list = new ArrayList<>(List.of("A", "B", "C"));
    List<String> subList = list.subList(0, 1); // subList: [A]

    subList.add("P"); // subList: [A, P]
    System.out.println(list); // [A, P, B, C]
    
    list.set(0, "AA"); // list: [AA, P, B, C]
    System.out.println(subList); // [AA, P]
    ```

    - 子字符串取得范围 左闭右开

- void replaceAll(UnaryOperator<E> operator)

- void sort(Comparator<? super E> comparator)

### 具体实现类

主要有

- ArrayList

底层是可扩容数组。

适合：

- 频繁按索引读取
- 主要在末尾添加
- 大多数普通场景

- LinkedList

底层是双向链表，实现Deque<E> 所以可以宣言：

```Java
Deque<String> deque = new LinkedList<>();
List<String> list = new LinkedList<>();
```

### list对象声明方式

#### new ArrayList()

普通可修改列表

```java
List<String> list = new ArrayList<>();

list.add("A");
list.remove("A");
list.set(0, "B");
```

#### Arrays.asList()

固定长度的List, Arrays是一个专门提供操作Array方法的类。

```java
List<String> list = Arrays.asList("1", "2");
list.set(0, "2");

list.add("3"); // 编译成功但是执行错误 UnsupportedOperationException
list.remove("1"); // 编译成功但是执行错误 UnsupportedOperationException
```

影响原数组

```java
String[] array = {"A", "B"};
List<String> list = Arrays.asList(array);
array[0] = "X";
System.out.println(list); // [X, B]
```

#### List.of()

创建不可修改的对象列表 并且不可以是null

```java
List<String> lst = List.of("AA", "AAA", "AAAA");

list.add("BB"); // 编译成功 但是执行错误 UnsupportedOperationException
list.set(0, "BB"); // 编译成功 但是执行错误 UnsupportedOperationException
list.remove("AA"); // 编译成功 但是执行错误 UnsupportedOperationException

List<String> lst2 = List.of("AA", "AAA", "AAAA", null); // 编译成功 但是执行空指针异常
```

但是在外层嵌套一层ArrayList就可以修改了 

```java
List<String> list = new ArrayList<>(List.of("AA", "AAA", "AAAA"));
// 这里实质上是把不可变的List.of创建的列表复制给了可变的ArrayList
list.add("BB");
list.set(0, "BB");
list.remove("AA");
```

#### List.copyOf()

类似List.of 属于浅拷贝语义 返回独立副本

元素不可被更改 但元素本身可能会被更改

```java
List<Foo> lst = new ArrayList<>();
lst.add(new Foo("Lil"));

List<Foo> copyList = List.copyOf(lst);
System.out.println(copyList); // [Lil]
lst.get(0).changeName("Rar"); // 因为是浅拷贝 所以lst和copyList的元素指向同一个实例
lst.add(new Foo("Aatrox")); // 即使原本的列表更改 复制出来的新数组不会变换
System.out.println(copyList); // [Rar] 
```

#### Collections.unmodifiedList()

类似List.copyOf 是原列表的只读视图。 Collections是一个专门提供操作Collection方法的类。
```java
List<Foo> lst = new ArrayList<>();
lst.add(new Foo("Lil"));

List<Foo> copyList = Collections.unmodifiableList(lst);
System.out.println(copyList); // [Lil]
lst.add(new Foo("Aatrox")); // 修改原列表 会影响视图
System.out.println(copyList); // [lil, Aatrox] 
```

## Set 集

> 内部元素不可以重复

### HashSet 

声明

```java
Set<String> set = new HashSet<>();
```

特点

- 不保证遍历顺序

```java
Set<String> set = new HashSet<>();

set.add("C");
set.add("A");
set.add("B");

System.out.println(set); // [A, B, C]
```

- 使用hasCode()和equals()判断重复

- 允许一个null元素

- 实现结构:哈希表

### LinkedHashSet 

声明

```java
Set<String> set = new LinkedHashSet<>();
```

特点

- 保持元素的插入顺序 重复添加也不会改变位置

```java
Set<String> set = new LinkedHashSet<>();

set.add("C");
set.add("A");
set.add("B");

System.out.println(set); // [C, A, B]

set.add("B"); // B不会被移动到最后
System.out.println(set); // [C, A, B]
```

- 使用hasCode()和equals()判断重复

- 允许一个null元素

- 实现结构：哈希表＋双向链表

### TreeSet 树集

声明

```java
Set<String> set = new TreeSet<>(); 
```

特点

- 自动排序

```java
Set<String> set = new TreeSet<>();

set.add("C");
set.add("Z");
set.add("A");
set.add("B");

System.out.println(set); // [A, B, C, Z]
```

- 使用compare()判断重复

- 不允许null元素 执行空指针异常

- 实现结构：红黑树

- 自定义排序

```java
Set<Integer> set = new TreeSet<>(Comparator.reverseOrder()); // 降序排列

set.add(30);
set.add(10);
set.add(20);

System.out.println(set); // [30, 20, 10]
```

```java
Set<String> set =
        new TreeSet<>(Comparator.comparingInt(String::length)); // 长度排序

set.add("AA");
set.add("BBB");
set.add("CC"); // CC与AA长度相同 被认为重复 所以不会加入到Set中 需要增加其他约束

System.out.println(set); // [AA, BBB]
```

```java
Set<String> set = new TreeSet<>(
        Comparator.comparingInt(String::length)
                  .thenComparing(Comparator.naturalOrder())
);// 如果长度相同 则按照字典排序

set.add("AA");
set.add("BBB");
set.add("CC"); // CC与AA长度相同 被认为重复 所以不会加入到Set中 需要增加其他约束

System.out.println(set); // [AA, CC, BBB]
```

- 额外方法

TreeSet 不只是普通的 Set，它还实现了 NavigableSet，可以进行范围查找

- first() 和 last() 

    - 取得首位元素

- lower() 

    - 严格小于指定值的`最大`元素：

- floor() 

    - 小于等于指定值的`最大`元素：

- higher()

    - 严格大于指定值的`最小`元素：

- ceiling()

    - 大于等于指定值的`最小`元素：

示例

```java
TreeSet<Integer> set = new TreeSet<>(); // 注意这里的类型是TreeSet<> 不是Set<>

set.add(10);
set.add(20);
set.add(30);

System.out.println(set.first());  // 10
System.out.println(set.last()); // 30
System.out.println(set.lower(10)); // null 
System.out.println(set.floor(10)); // 10
System.out.println(set.higher(20)); // 30
System.out.println(set.ceiling(20)); // 20
```

### 三个子类判断插入元素是否重复的方法

> 哈希集 哈希链集 主要根据hashCode() 以及equal进行判等：

两者关系

- 相等的两个元素哈希值一定相同

- 反过来不一定对

```java
set.add(a);
set.add(b);
```

如果a.equals(b) 并且二者的哈希值符合规范，那么集合认为它们重复。

> TreeSet主要根据比较结果（可自定义）判断：

```java
Set<String> set =
        new TreeSet<>(Comparator.comparingInt(String::length)); // 长度排序

set.add("AA");
set.add("BB");
```

AA, BB长度相同 所以被认为重复

### Set.of()

类比List.of(), 不可修改，不可以有null，因为是Set所以不可以有重复。

```java
Set.of("A", "A"); // IllegalArgumentException
Set.of("A", null); // NullPointerException
```

### 可变键陷阱

## Queue 队列

### 声明

```java
Queue<String> queue = new ArrayQueue<>();
```

### 使用

| 操作   | 失败时抛异常      | 失败时返回特殊值   |
| ---- | ----------- | ---------- |
| 添加   | `add(e)`    | `offer(e)` |
| 删除队首 | `remove()`  | `poll()`   |
| 查看队首 | `element()` | `peek()`   |

```java
Queue<String> queue = new ArrayDeque<>();

queue.remove();  // NoSuchElementException
queue.element(); // NoSuchElementException

queue.poll();    // null
queue.peek();    // null
```


### Deque 双端队列

`Deque` /deck/ 是双端队列 可以在两端进行添加删除查看操作

```java
Deque<String> deque = new ArrayDeque<>();
```

| 位置   | 抛异常方法           | 返回特殊值方法        |
| ---- | --------------- | -------------- |
| 头部添加 | `addFirst()`    | `offerFirst()` |
| 尾部添加 | `addLast()`     | `offerLast()`  |
| 头部删除 | `removeFirst()` | `pollFirst()`  |
| 尾部删除 | `removeLast()`  | `pollLast()`   |
| 查看头部 | `getFirst()`    | `peekFirst()`  |
| 查看尾部 | `getLast()`     | `peekLast()`   |

Deque实现了继承自Queue的接口 所以当作普通queue来使用

- 可以使用上面的peek(), poll()等方法

因为双端都可以操作 所以可以模拟栈

```java
Deque<String> stack = new ArrayDeque<>();

stack.push("A"); // Pushes an element onto the stack represented by this deque. 相当于前文提到的AddFirst
stack.push("B");
stack.push("C");

System.out.println(stack.pop()); // C removes and returns the first element of this deque. 相当于前文提到的RemoveFirst
System.out.println(stack.pop()); // B
```

> ArrayDeque 不允许加入 null，因为 poll()、peek() 等方法需要用 null 表示空队列。

### PriorityQueue 优先队列



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
public static <T> T geta(List<T> list) {
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

### 多重上界

规则

- 类在最前面 后面跟一个或多个接口

```java
class Foo<T extends Number & Comparable<T>> { }
class Foo2<T extends Number & Comparable<T> & AutoCloseable> { }
```

## 协变关系

泛型没有协变关系 

```java
List<Dog> dogs = new ArrayList<>();

List<Animal> animals = dogs; // Compile Error
```

数组有协变关系 但是类型不一定安全

```java
Animal[] animals = new Dog[3];
animals[0] = new Dog();
animals[1] = new Cat(); // 编译通过但执行错误java.lang.ArrayStoreException
```

## 如果使其有协变关系？ 使用通配符？

> 表示未知类型

- 种类

```java
List<?> // 无界通配符
// 例如：
List<?> objects = List.of(new Cat(), new Dog(), new Animal());

List<? extends Number> // 上界通配符
// 例如：
List<Dog> list = List.of(new Dog(), new Dog());
List<? extends Animal> animals = list;

List<? super Integer>  // 下界通配符
// 例如
List<Animal> animals = new ArrayList<>();
List<? super Dog> dogs = animals;
```

### 上界通配符 WILD CARD

写法：`List<? extends Animal> list;`, 意思是定义一个可以匹配Animal以及子类的列表


### 下界通配符
写法：`List<? super Dog> list;`, 意思是定义一个可以匹配Dog以及父类（Animal, Object）的列表


### PECS原则

Producers Extends, Consumers Super.

> 如果读取集合 使用extends

```java
static double sum(List<? extends Number> list) {
    double total = 0;

    for (Number n : list) {
        total += n.doubleValue();
    }

    return total;
}
```

> 如果写入集合 使用super

```java
static void addIntegers(List<? super Integer> list) {
    list.add(10);
    list.add(20);
}
```

