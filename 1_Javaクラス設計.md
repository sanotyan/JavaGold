# 1章 Javaクラス設計

1章はJavaのクラス設計についてです。  
この章ではSilverから比べても新しいクラスや知識は多くありませんが、その分理解していないと解けない問題が多く出題される傾向にあります。  
## 1-1 switch
以下のコードを実行した結果を述べよ。
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
            System.out.println("a");
        case 1:
            System.out.println("b");
        default:
            System.out.println("c");
        }
    }
}
```  
答え：NullPointerExceptionが発生する。  
Swichクラスのメンバであるiは初期化が行われていないため、nullが代入されています。  
switch文では参照型の値の比較はequalsを用いて行うため、NullPointerExcepitonが発生します。
## 1-2 修飾子
### 1-2-1 static
以下のコードを実行した結果を述べよ。
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
### 1-2-2 final
以下のコードを実行した結果を述べよ。
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

## 1-3 Enum
### 1-3-1 Enum.Values()
以下のコードを実行した結果を述べよ。
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
                System.out.println("a");
                break;
            case B:
                System.out.println("b");
                break;
            default:
                System.out.println("c");
            }
        }
    }
}
```

## 1-4 static import
### 1-4-1 語順
以下のコードを実行した結果を述べよ。
```java
import static java.lang.Math.PI;

class Main {
	public static void main(String args[]) {
		System.out.println(Math.PI);
	}
}
```


[戻る](https://github.com/sanotyan1202/JavaGold)
