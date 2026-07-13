```Java
interface AA {
    void func();
}

class BB implements AA {
    void func() {
        System.out.println("qwe");
    }
}
```

```Java
class Test0 {
    public void foo() {
        System.out.print("Afoo ");
    }
}

public class Test extends Test0 {
    public void foo() {
        System.out.print("Bfoo ");
    }

    public static void main(String[] args) {
        Test0 test0 = new Test();
        Test test = (Test) test0;

        test.foo();
        test0.foo();
    }
}
```



```Java
class Super {
    public void out() {
        System.out.println("Super");
    }
}

class Sub extends Super {
    public void out() {
        System.out.println("Sub");
    }
}

class Main {
    public static void main(String args[]) {
        function(new Sub());
    }

    static void function(Super s) {
        s.out();
    }
}
```