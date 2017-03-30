# 1章 Javaクラス設計

1章はJavaのクラス設計についてです。  
この章ではSilverから比べても新しいクラスや知識は多くありません。  
その分、理解していないと解けない問題が出題される傾向にあります。  
## 1-1 switch
##### 問.以下のコードを実行した結果を述べよ。
```java
class Main {
    public static void main(String[] args) {
        new Switch().execSwitch();
    }
}
class Switch {
    Integer i;
    public void execSwitch() {
        switch(i) {
        case 0:
            System.out.print("a");
        case 1:
            System.out.print("b");
        default:
            System.out.print("c");
        }
    }
}
```  
答え：NullPointerExceptionが発生する。  

Swichクラスのメンバであるiは初期化が行われていないため、nullが代入されています。  
switch文では参照型の値の比較はequalsを用いて行うため、NullPointerExcepitonが発生します。  
  
##### 問.以下のコードを実行した結果を述べよ。
```java
class Main {
    public static void main(String[] args) {
        new Switch().execSwitch();
    }
}
class Switch {
    Integer i = 1;
    public void execSwitch() {
        switch(i) {
        case 0:
            System.out.print("a");
        case 1:
            System.out.print("b");
        default:
            System.out.print("c");
        }
    }
}
```
答え：bc  
  
iに1が代入されているため、case 1以下の処理が実行されます。  
caseの処理の終わりにbreakが記述されていないためdefault以下の処理も実行され"c"が出力されます。  

## 1-2 修飾子
##### 問.以下のコードを実行した結果を述べよ。
```java
class Main {
    private String val = "a";
    public static void main(String[] args) {
        System.out.println("a");
        System.out.println(new String("a"));
        System.out.println(new Main().val);
        System.out.println(val);
    }
}
```  
答え：最終行でコンパイルエラーが発生する。  
  
staticメソッドから非staticメンバであるvalにアクセスすることはできません。  
staticメソッドやメンバはアプリケーション実行時にインスタンス化され、実行中は常にアクセスが可能です。  
しかし、非staticメソッドやメンバは「new Main().val」のようにインスタンス化してアクセスする必要があります。  
  
##### 問.以下のコードを実行した結果を述べよ。
```java
public class Foo {
    final int i = 0;
    static {
        i = 1;
    }
    {
        i = 2;
    }
    public Foo(){
       i = 2;
    }
}
```
答え：staticイニシャライザでコンパイルエラーが発生する。  
  
final修飾子を持つメンバは一度だけ初期化することができますが、問題文ではイニシャライザ、コンストラクタでも代入しておりコンパイルエラーとなります。  

## 1-3 Enum
##### 問.以下のコードを実行した結果を述べよ。
```java
class Main {
    public static void main(String[] args){
        new Switch().execSwitch();
    }
}
enum Foo {
    A(1), B(2), C(0);
    private int val;
    Foo(int val){
        this.val = val;
    }
}
class Switch{
    public void execSwitch(){
        for(Foo f : Foo.values()){
            switch(f){
            case A:
                System.out.print("a");
            case B:
                System.out.print("b");
            default:
                System.out.print("c");
            }
        }
    }
}
```
答え：abcbcc  
  
EnumクラスのValuesメソッドはEnumクラスのインスタンスを配列で返します。  
配列の順番は宣言順です。  

## 1-4 Static Import
##### 問.以下のコードを実行した結果を述べよ。
```java
import static java.lang.Math.PI;

class Main {
    public static void main(String args[]) {
        System.out.println(PI);
    }
}
```  
答え：import文でコンパイルエラーが発生する。  
  
Static Importの記述はimoport staticです。  

[次へ](https://github.com/sanotyan1202/JavaGold/blob/master/2_%E3%83%9D%E3%83%AA%E3%83%A2%E3%83%95%E3%82%A3%E3%82%BA%E3%83%A0.md)　
[戻る](https://github.com/sanotyan1202/JavaGold)
