1.Java開発環境の説明で正しいものはどれですか。1つ選択してください。
A. Java開発環境はJDK、JRE、IDEのセットで提供されている
B. Java開発環境の準備を行う際、JDKの前にIDEをインストールする必要がある
C. Java開発環境では、最初にJREをインストールする必要がある
D. 利用中のOS用のJDKをインストールするとJava開発環境がセットアップされる
E. Java開発環境はすべてのOSでデフォルトでインストールされている


2.実行時のパフォーマンスを高めるために行われているものはどれですか。1つ選択してください。
A. 頻繁に実行するコードを最適化する
B. ガベージコレクションを優先的に行う
C. コードを自動的に並列化し実行する
D. 基本データ型の値をラッパークラスのオブジェクトへ変換する


3.JDKが提供する機能はどれですか。2つ選択してください。
A. データベースエンジン
B. IDE（Integrated Development Environment）
C. 開発ツール（javac、jdbなど）
D. バージョン管理ツール
E. Java SE API


4.main()メソッドの引数として定義した場合、適切にコンパイルと実行ができる引数はどれですか。3つ選択
してください。
A. String[] args
B. String args
C. String args[]
D. String... args
E. Object[] args


5.main()メソッドとして実行可能なものはどれですか。2つ選択してください。
A. public void static main(String[] args)
B. public static void main(String[] duke)
C. public static final void main(String[] args)
D. static void main(String[] args)
E. public static int main(String[] args)


6.次のコードを確認してください。
```Java
public class Test { 
    public static void main(String[] args) { 
        String str = "";
        for (int i = 0; i < 3; i++) { 
            str += (args[i] + ":"); 
        }
        System.out.println(str);
    }
}
```
このコードに対してコンパイルが成功後、下記のコマンドを実行すると、どのような結果になりますか。1つ選択してください。
> java Test "1 2" "3 4" 
A. 1:2:3
B. 1:2:3:4:
C. 1 2:3 4:
D. 実行時エラーが発生する

7.次のコードを確認してください。
```Java
public class Sample {
    public static void main(String[] args) {
        for (int i = 0; i < args.length; i++) {
            int num = Integer.parseInt(args[i]);
            System.out.println(num + 1);
        }
    }
}
```
このコードに対して下記のコマンドを実行すると、どのような結果になりますか。1つ選択してください。
> java Sample 0 1 2 
A. 0 1 2
B. 1 2 3
C. 0 0 0
D. 実行時エラーが発生する

8.次のコードを確認してください。
```Java
public class Sample {
    public static void main(String[] args) {
        System.out.println(args.length);
    }
}
```
このコードに対してコンパイルが成功後、下記のコマンドを実行すると、どのような結果になりますか。1つ選択してください。
> java Sample 
A. 0
B. 何も出力されない
C. null
D. 実行時エラーが発生する


9.次のコードを確認してください。
```Java
public class Test {
    public static void main(String[] args) {
        System.out.println("Hello");
    }
    
}
```
このコードに対してコンパイルが成功後、下記のコマンドを実行すると、どのような結果になりますか。1つ選択してください。
> java Test.java 
A. Hello
B. 何も出力されない
C. コンパイルエラーが発生する
D. 実行時エラーが発生する


10.次のコードを確認してください。
```Java
class Foo {
    public static int func() {
        return 10;
    }
}
public class Sample {
    public static void main(String[] args) {
        System.out.print(Foo.func());
        System.out.print("Sample");
    }
}
```
このコードに対してコンパイルが成功後、下記のコマンドを実行すると、どのような結果になりますか。1つ選択してください。
> java Sample.java 
A. 10Sample
B. 何も出力されない
C. コンパイルエラーが発生する
D. 実行時エラーが発生する


11. クラス定義の際、ソースコードに定義する順序として適切なものはどれですか。1つ選択してください。
A. class-import-package
B. import-class-package
C. package-class-import
D. package-import-class
E. import-package-class


12. クラスのパッケージ宣言として適切ではないものはどれですか。1つ選択してください。
A. パッケージ名は.（ドット）でつなぐことでサブパッケージの宣言が可能
B. 1つのソースファイルに複数のパッケージ宣言が可能
C. パッケージ名が異なっていれば同名のクラス定義が可能
D. パッケージ宣言を行わないクラス定義も可能


13. 以下のパッケージ階層があります。
```Bash
──pack1
    ├─pack2
    │  ├─Blue class
    │  └─pack3
    │      └─White class
    └─Red class
```
上記に加え、以下のクラスがあります。
```Java
public class PackageTest {
    Red r;
    Blue b;
    While w;
}
```
どのコードをPackageTestクラスに追加すれば、正しくコンパイルできますか。3つ選択してください。
A. package pack3;
B. package pack1;
C. package pack1.pack2;
D. import pack1.pack2.*;
E. import pack1.Blue;
F. import pack1.pack2.pack3.*;


14. 次のコードを確認してください。
- ソースファイル名：Test1.java
```Java
package pac1; 

public class Test1 {
    public static void main(String[] args) {
        String str = "Hello";
        System.out.print(str);
        Test2 test2 = new Test2(); 
        test2.foo();
    }
}
```
- ソースファイル名：Test2.java
```Java
package pac1.pac2; 

public class Test2 {
    public void foo() {
        System.out.println("World");
    }
}
```
Test1クラスをどのように変更すれば、Test1クラスをコンパイル、および実行できますか。3つ選択してください。（3つのうちいずれか1つを変更すれば、設問の条件を満たします。）
A. 7行目を「pac1.pac2.Test2 test2 = new Test2();」に変更
B. 7行目を「pac1.pac2.Test2 test2 = new pac1.pac2.Test2();」に変更
C. 7行目を「pac1.*.Test2 = new Test2();」に変更
D. 2行目に「import pac1.*;」を挿入
E. 2行目に「import pac1.pac2.*;」を挿入
F. 2行目に「import pac1.pac2.Test2;」を挿入


15. クラスファイルの依存関係をパッケージレベルやクラスレベルで表示するコマンドは、どれですか。1つ選択してください。
A. jdeps
B. jlink
C. javap
D. jshell


16. 基本データ型の変数宣言ではないものはどれですか。1つ選択してください。
A. int i = 0;
B. double d = 3.14;
C. boolean b = true;
D. char c = '\n';
E. String s = "Hello";


17. 変数の初期化として適切なものはどれですか。1つ選択してください。
A. char c1, char c2, char c3 = 'A'
B. int i1, i2, i3 = 10;
C. double d1 = 1.14, double d2 = 1.73, double d = 2.23;
D. x = 100, y = 'B', z = null;

18.19

20. 次のコードを確認してください。
```Java
public class Test {
    public static void main(String[] args) {
        var v1 = 'J';
        var v2 = 5_23;
        var v3 = 3.14_15f;
        System.out.println(v1+" : "+v2+" : "+v3); 
    }
}
```
このコードに対してコンパイルが成功後、下記のコマンドを実行すると、どのような結果になりますか。1つ選択してください。
A. J : 5_23 : 3.14_15
B. J : 523 : 3.1415
C. 3行目でコンパイルエラーが発生する
D. 4行目でコンパイルエラーが発生する
E. 5行目でコンパイルエラーが発生する
F. 実行時エラーが発生する


21. 次のコードを確認してください。
```Java
public class Test {
    public static void main(String[] args) {
        var v1;
        v1 = 100;
        final var v2 = 123;
        System.out.print(v1 + " : " + v2)
    }
}
```
このコードに対してコンパイル、および実行すると、どのような結果になりますか。1つ選択してください。
A. 100 : 123
B. 3行目でコンパイルエラーが発生する
C. 4行目でコンパイルエラーが発生する
D. 5行目でコンパイルエラーが発生する
E. 実行時エラーが発生する

22

23. 次のコードを確認してください。
```Java
public class Test {
    public static void main(String[] args) {
        var v1 = 10, v2 = 20;
        var v3 = v1;
        System.out.print(v1 + " : " + v2 + " : " + v3)
    }
}
```
このコードに対してコンパイル、および実行すると、どのような結果になりますか。1つ選択してください。
A. 10 : 20 : 10
B. 3行目でコンパイルエラーが発生する
C. 4行目でコンパイルエラーが発生する
D. 実行時エラーが発生する

24


25. 配列名の定義として適切なものはどれですか。2つ選択してください。
A. String i[3];
B. Byte b;
C. Object o[];
D. int[] i;
E. double[0] d;


26. 配列の初期化として適切なものはどれですか。2つ選択してください。
A. int i[] = new int[3]{10, 20, 30};
B. int[] i = {10, 20, 30};
C. int[] i = new int[]{10, 20, 30};
D. int i[3] = {10, 20, 30};


27. 次のコードを確認してください。
```Java
public class Test {
    public static void main(String[] args) {
        boolean b[] = new boolean[3]; 
        int i[] = {1, 2, 3};
        String s[] = new String[5];
        System.out.println(b[2] + " : " + i[1] + " : " + s[3]);
    }
}
```
このコードに対してコンパイル、および実行すると、どのような結果になりますか。1つ選択してください。
A. true : 2 : null
B. false : 2 : null
C. true : 2 :
D. false : 2 : false : 2 :
E. 6行目でコンパイルエラーが発生する
F. 6行目で実行時エラーが発生する


28. 次のコードを確認してください。
```Java
public class Test {
    public static void main(String[] args) {
        int[] ary = {10, 20, 30};
        int i = ary.length;
        while(i >= 0) {
            System.out.println(ary[i--]);
        }
    }
}
```
このコードに対してコンパイル、および実行すると、どのような結果になりますか。1つ選択してください。
A. 0 : 30 : 20 : 10 :
B. 30 : 20 : 10 :
C. 20 : 10 :
D. コンパイルエラーが発生する
E. 実行時エラーが発生する


29. 次のコードを確認してください。
```Java
public class Test {
    public static void main(String[] args) {
        String[] ary1 = {"A", "B"}; 
        String[] ary2 = {"A", "B"}; 
        String[] ary3 = ary1;
        System.out.print((ary1 == ary2) +" : ");
        System.out.print(ary1 == ary3);
    }
}
```
このコードに対してコンパイル、および実行すると、どのような結果になりますか。1つ選択してください。
A. true : true
B. true : false
C. false : true
D. false : false
E. 実行時エラーが発生する

30. 二次元配列の宣言、初期化として適切なものはどれですか。2つ選択してください。
A. int[][] i = new int[2][2]{{10, 20}, {20, 30}};
B. int i[][] = new int[2][];
    i[0] = new int[2]; 
    i[1] = new int[3];
C. int[][] i = {{10, 20}, {30, 40}, {50, 60}};
D. int i[][] = new int[][2];
    i[0] = new int[2]; 
    i[1] = new int[3];

31. 次のコードを確認してください。
```Java
public class Test {
    public static void main(String[] args) {
        int[][] ary = {{0},{0,1},{0,1,2},{0,1,2,3},{0,1,2,3,4}}; 
        for(int i = 0; i < ary.length ;i++) { 
            System.out.print( /* insert code here */ );
        }
    }
}
```
5行目にどのコードを挿入すれば「01234」と出力されますか。2つ選択してください。（2つのうち、いずれか1つを挿入すれば、設問の条件を満たします。）
A. ary[0][i]
B. ary[i][i]
C. ary[i][0]
D. ary[4][i]
E. ary[i][4]


32. 次のコードを確認してください。
```Java
public class Test {
    public static void main(String[] args) {
        int[][] i = {{10, 20, 30}, {40, 50, 60}}; 
        System.out.println(i[0]); 
    }
}
```
このコードをコンパイル、および実行すると、どのような結果になりますか。1つ選択してください。
A. 10
B. 40
C. 何も出力されない
D. 先頭配列のハッシュ値が出力される


33. 次のコードを確認してください。
```Java
public class Test {
    public static void main(String[] args) {
        int[][] array = {{10, 20, 30}, {40, 50}, {60}};
        System.out.print(array.length + " : "); 
        System.out.print(array[1].length); 
    }
}
```
このコードをコンパイル、および実行すると、どのような結果になりますか。1つ選択してください。
A. 3 : 2
B. 6 : 2
C. コンパイルエラーが発生する
D. 実行時エラーが発生する


34. 次のコードを確認してください。
```Java
public class Test {
    public static void main(String[] args) {
        int[][] array = {{10, 20, 30}, {40, 50}, {60}};
        System.out.print(array.length + " : "); 
        System.out.print(array[1].length); 
    }
}
```
このコードをコンパイル、および実行すると、どのような結果になりますか。1つ選択してください。
A. 3 : 2
B. 6 : 2
C. コンパイルエラーが発生する
D. 実行時エラーが発生する


35. 次のコードを確認してください。
```Java
public class Test {
    public static void main(String[] args) {
        System.out.print("Result: " + 1 + 2 + 3); 
        System.out.print(" Result: " + 1 + 2 * 3); 
    }
}
```
このコードをコンパイル、および実行すると、どのような結果になりますか。1つ選択してください。
A. Result: 6 Result: 7
B. Result: 6 Result: 9
C. Result: 15 Result: 16
D. Result: 123 Result: 16
E. Result: 123 Result: 123


36. 次のコードを確認してください。
```Java
class DecrementSample {
    public static void main(String[] args) {
        int num = 3;
        num --;
        System.out.print(--num);
        System.out.print(num);
    }
}
```
このコードをコンパイル、および実行すると、どのような結果になりますか。1つ選択してください。
A. 11
B. 12
C. 21
D. 22


36. 次のコードを確認してください。
```Java
class LogicalTest {
    public static void main(String[] args) {
       boolean flag1 = (1 != 0) && (2 != 3); 
       boolean flag2 = (4 != 4) || (4 == 4);
       System.out.print("flag1: " + flag1 + " flag2: " + flag2); 
    }
}
```
このコードをコンパイル、および実行すると、どのような結果になりますか。1つ選択してください。
A. flag1: true flag2: true
B. flag1: true flag2: false
C. flag1: false flag2: true
D. flag1: false flag2: false


38. 次のコードを確認してください。
```Java
class EqualTest {
    public static void main(String[] args) {
       boolean flag1 = (1 != 0) && (2 != 3); 
       boolean flag2 = (4 != 4) || (4 == 4);
       System.out.print("flag1: " + flag1 + " flag2: " + flag2); 
    }
}
```
このコードをコンパイル、および実行すると、どのような結果になりますか。1つ選択してください。
A. flag1: true flag2: true
B. flag1: true flag2: false
C. flag1: false flag2: true
D. flag1: false flag2: false

xx. 次のコードを確認してください。
```Java
public class Message {
    public static void main(String args[]) {
        StringBuilder sb = new StringBuilder(); 
        String msg = "Thankyou";

        sb.append("Thank").append("you"); 
        if(msg == sb.toString()) {
            System.out.println("Same Object");  
        }
        if(sb.equals(msg.toString())) {
            System.out.println("Same String");
        }
    }
}
```
このコードをコンパイル、および実行すると、どのような結果になりますか。1つ選択してください。
1. A. Same Object Same String
2. B. Same String
3. C. Same Object
4. D. 何も出力されない



