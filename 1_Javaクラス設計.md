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
## 1-2 static
### 1-2-1 staticへのアクセス
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


[戻る](https://github.com/sanotyan1202/JavaGold/blob/master/0_Introduction.md)
