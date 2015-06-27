# fraction class
C#で分数の計算を行うクラス
このクラスはC#上で分数の計算を行うクラスです。int型やdouble型といった組み込み型と同様に四則演算の演算子（+,-,×,÷）や大小比較を使うことができます。

### プロジェクトの構成
本プロジェクトファイルはvisual studioで作られたものです。構成は以下のようになっています。
* Fraction: fractionクラス本体
* FractionTest: fractionクラスの動作を確認するためのFormプロジェクト

### 導入
1. dllの参照  
「Fraction/bin」フォルダ内にある「fraction.dll」を使いたいプロジェクトから参照してください。visual studioでの参照の方法は[こちら](https://msdn.microsoft.com/ja-jp/library/7314433t(v=vs.90).aspx)

2. usingディレクティブの追加  
fractionクラスを使いたいコードの頭に以下のusingディレクティブを追加してください。

    ```csharp
    using fraction; //注意：小文字です
    ```
### 使用例

fractionクラスはコンストラクタを明示しなければいけないこと以外はint型やdouble型などと同じように使えます。  
コンストラクタは以下の4種類あります。

```csharp
Fraction(); //引数なし（0として扱われます）
Fraction(int numerator,int denominator); //分子（numerator）と分母（denominator）を指定。最も一般的な使い方
Fraction(double x); //小数を分数として扱う（例:0.25を入力すると1/4として扱われます）
Fraction(int x); //整数を分数として扱う（x/1という形の分数として扱われます）
```

公開プロパティ（クラス外部からアクセスできる変数）は以下の2つです。  

```csharp
int Numerator; //分子の値
int Denominator; //分母の値
double DecimalValue; //小数値（1/2なら0.5が返される）
```
また、負数の場合は分子に負号がつきます（分母は常に正数となります）。


#### 演算
本クラスでは以下のような計算ができます。  

* 分数同士の四則演算および分数と整数の四則演算  
通分や約分は自動的に行われます
```csharp
Fraction x = new Fraction(1,2); //x = 1/2
Fraction y = new Fraction(1,3); //y = 1/3
int a = 2;
//加算
Fraction z1 = x + y; //z1 = 5/6
Fraction b1 = x + a; //b = 5/2
//減算
Fraction z2 = x - y; //z2 = 1/6
Fraction b2 = a - x; //b2 = 3/2
//乗算
Fraction z3 = x * y; //z3 = 1/6
Fraction b3 = a * x; //b3 = 1/1
//除算
Fraction z4 = x / y; //z4 = 3/2
Fraction b4 = a / x; //b4 = 4/1
```

* 比較演算
```csharp
Fraction x = new Fraction(1,2); //x = 1/2
Fraction y = new Fraction(1,3); //y = 1/3
//等号
if(x == y){}
//
if(x != y){}
//不等号
if(x > y){}
if(x < y){}
if(x >= y){}
if(x <= y){}
```
