# 1章 Javaクラス設計

## 1-1 switch文

#### 1-1-1 nullをswitchする
問.以下のコードを実行した結果を述べよ。
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
## 1-2 修飾子
### 1-2-1 static
問.以下のコードを実行した結果を述べよ。
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
問.以下のコードを実行した結果を述べよ。
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

```java
import static java.lang.Math.PI;

class Main {
	public static void main(String args[]) {
		System.out.println(Math.PI);
	}
}
```


[戻る](https://github.com/sanotyan1202/JavaGold)
