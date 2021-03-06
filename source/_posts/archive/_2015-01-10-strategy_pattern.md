title: Strategyパターン
date: 2015-01-10 14:34:03
tags: DesignPatterns
---

## パターンについて
Strategyパターンは交換可能な振舞いをカプセル化し、委譲を使って使用すべき振舞いを決定します。
主要な処理を行っているコードの中で一部動的に振舞いを変更させたい場合に利用し、
コードの中で動的に振舞い変更したい場合は、if文なので条件分岐しがちになりますが
Strategyを利用することで主要な処理に対して影響を与えず、1つのステートメントで動的な振舞いを定義することができます。

>HeadFirstデザインパターンでの定義
>
>一連のアルゴリズムを定義してそれぞれをカプセル化し、それらを交換可能にする。
>Strategyパターンによって、アルゴリズムを使用するクライアントとは独立して、アルゴリズムを変更できる


## パターン構造
![strategy_pattern](/image/DesignPattern/strategy.png)
**構成要素**
Context :　インタフェース Strategy を利用するクラス。
Strategy :　アルゴリズムに共通のインタフェース。Context オブジェクトはこのインタフェースを使用する。
ConcreteStrategy :　インタフェース Strategy を実現する具象クラス。様々なアルゴリズムを実装する。


## サンプル
鴨の鳴き方(振舞い)を動的に変える場合

・鳴き方インタフェース
``` java(Strategy)
public interface QuackBehavior {
	public void quack();
}
```

・鳴き方1(ConcreteStrategyA)
``` java
public class Quack implements QuackBehavior {
	public void quack() {
		System.out.println("ガーガー");
    }
}
```

・鳴き方2(ConcreteStrategyB)
``` java
public class Squeak implements QuackBehavior {
	public void quack() {
		System.out.println("キューキュー");
    }
}
```

・鴨クラス(Context)
``` java
public class Duck {

	QuackBehavior quackBehavior;

	public Duck() {
		quackBehavior = new Quack();
	}

	public void performQuack() {
		quackBehavior.quack();
	}

	public void setQuackBehavior(QuackBehavior qb) {
		quackBehavior = qb;
	}
}
```

・実行コード
``` java
public class Client {

	public static void main(String[] args) {
		Duck duck = new Duck();
		duck.performQuack();
		model.setQuackBehavior(new Squeak());
		duck.performQuack();
	}
}

// 実行結果
// ガーガー
// キューキュー
```
