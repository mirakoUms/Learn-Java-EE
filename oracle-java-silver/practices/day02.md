```Java
public class Test {
    public static void main(String args[]) {
        int[] array = new int[] {10,20,30}; 

        for (final var v : array) {
            System.out.print(v + " ");
        }
    }
}
```



```Java
class Test {
    int foo(double d) {
        System.out.println("one");
        return 0;
    }

    String foo(double d) {
        System.out.println("two");
        return null;
    }

    double foo(double d) {
        System.out.println("three");
        return 0.0;
    }

    public static void main(String[] args) {
        new Test().foo(4.0);// 编译错误
    }
}
```


```Java
class Test {
    static int staNum = 3;

    public static void main(String[] args) {
        Test test = new Test();

        test.staNum++;
        Test.staNum++;
        test.staNum++;

        System.out.println(Test.staNum + "" + test.staNum);
    }
}
```

カプセル化のメリットとして正しい説明は、以下のうちどれですか。
2つ選択してください。
A. 呼び出し元を変更せずにメソッド内の実装を変更できる
B. オブジェクトのデータを隠ぺいできる
C. クラスを同一パッケージに定義できる
D. 同一クラスの複数のインスタンスを安全に生成できる