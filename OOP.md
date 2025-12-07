## **クラス**とは、その内部に手続きや関数を定義できるユーザ定義型である。

クラスを使うことで、データとそのデータを操作する手続きや関数を一つの単位としてまとめることができる。これにより、関連する機能を論理的にグループ化し、コードの再利用性と保守性を向上させることができる。

例：
```java
class Rectangle {
    private double width;
    private double height;
    
    public Rectangle(double w, double h) {
        width = w;
        height = h;
    }
    
    public double area() {
        return width * height;
    }
}
```

## **オブジェクト指向プログラミング**とは、クラス階層に焦点を当てるプログラミングである。
クラス階層は、**実行時多相性**と**カプセル化**を提供する。

- **実行時多相性**：基底クラスやインターフェースの参照を通じて、派生クラスのオブジェクトに対して適切なメソッドを実行時に選択できる機能。これにより、同じインターフェースで異なる実装を扱える。
- **カプセル化**：データとその操作を一つの単位にまとめ、外部からの直接アクセスを制限することで、データの整合性を保つ仕組み。

クラス階層を活用することで、コードの拡張性が高まり、新しい機能を追加する際に既存のコードを変更せずに済む。

例：
```java
abstract class Shape {
    public abstract double area();  // 実行時多相性
}

class Circle extends Shape {
    private double radius;
    
    public Circle(double r) {
        radius = r;
    }
    
    @Override
    public double area() {
        return Math.PI * radius * radius;
    }
}
```

## **オブジェクト**は、メモリ上で連続している一つの領域である。

クラスから生成された実体がオブジェクトである。オブジェクトは、クラスで定義されたデータメンバの値を持ち、メンバ関数を呼び出すことができる。メモリ上で連続しているという特性により、効率的なアクセスが可能になる。

例：
```java
Rectangle rect = new Rectangle(10.0, 5.0);  // rectがオブジェクト
double a = rect.area();                     // オブジェクトのメソッドを呼び出し
```

## オブジェクトの生存期間は、そのコンストラクタが実行を完了した時点から、デストラクタが実行を開始する時点までだ。

- **コンストラクタ**：オブジェクトの生成時に自動的に呼び出される特殊なメソッド。オブジェクトの初期化を行う。
- **ガベージコレクション**：Javaでは、使用されなくなったオブジェクトは自動的にガベージコレクタによって回収される。ただし、ファイルやネットワーク接続などのリソースは、明示的にクローズする必要がある。

この生存期間の管理により、リソースの適切な取得と解放が保証され、メモリリークやリソースリークを防ぐことができる。Javaでは、try-with-resources文を使用することで、リソースの自動解放が可能になる。

例：
```java
class Resource implements AutoCloseable {
    private int[] data;
    
    public Resource() {
        data = new int[100];  // コンストラクタ：リソース取得
    }
    
    @Override
    public void close() {
        // リソース解放（ガベージコレクタが自動的にメモリを回収）
        data = null;
    }
}

// 使用例
try (Resource res = new Resource()) {
    // リソースを使用
}  // 自動的にclose()が呼ばれる
```

（参考文献）
ビャーネ・ストラウストラップ. プログラミング言語C++ 第4版. SBクリエイティブ株式会社. Kindle 版. 
なお、具体例は Java のコードとした。