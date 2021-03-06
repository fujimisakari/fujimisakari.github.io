title: Observerパターン
date: 2015-01-11 02:16:47
tags: DesignPatterns
---

## パターンについて
状態が変化したときにオブジェクトへ通知します。
あるオブジェクト（通知元）の状態変化を不特定多数のオブジェクト（通知先）に知らせたいときに利用します。
監視対象オブジェクトを中継させることで、通知元オブジェクトは通知先オブジェクトのことを知らなくても定義できます。

>HeadFirstデザインパターンでの定義
>
>オブジェクト間の1対多の依存関係を定義し、あるオブジェクトの状態が変化すると、
>それに依存しているすべてのオブジェクトが自動的に通知されるようにします。


## パターン構造
![observer_pattern](/image/DesignPattern/observer.png)
**構成要素**
Observer :　観測者のインタフェース。Subject から呼び出される update メソッドを定義する。
ConcreteObserver :　Observerインタフェースを実装する具象クラス。update メソッドの中で自分の状態を変更する。
Subject :　観測対象の抽象クラス。notifyObservers メソッドの中で登録している Observer に対して update を呼び出す。
ConcreteSubject	:　Subjectクラスを継承する具象クラス。観測者の具体的なデータを保持する。


## サンプル
気象観測所(subject)が観測者(observer)に対して気象情報を通知する場合

・観測者インタフェース(Observer)
``` java
public interface Observer {
	public void update(float temp, float humidity, float pressure);
}
```

・観測者の具象クラス(ConcreteObserver)
``` java
public class CurrentConditionsDisplay implements Observer {
	private float temperature;
	private float humidity;
	private Subject weatherData;

	public CurrentConditionsDisplay(Subject weatherData) {
		this.weatherData = weatherData;
		weatherData.registerObserver(this);
	}

	public void update(float temperature, float humidity) {
		this.temperature = temperature;
		this.humidity = humidity;
		display();
	}

	public void display() {
		System.out.println("現在の気象状況: 温度" + temperature + "度 湿度" + humidity + "%");
    }

}
```

・気象観測所インタフェース(Subject)
``` java
public interface Subject {
	void registerObserver(Observer o);

	void removeObserver(Observer o);

	void notifyObservers();
}

```

・気象観測所の具象クラス(ConcreteSubject)
``` java
public class WeatherData implements Subject {
	private ArrayList<Observer> observers;
	private float temperature; // 温度
	private float humidity; // 湿度

	public WeatherData() {
		this.observers = new ArrayList<Observer>();
	}

	public void registerObserver(Observer o) {
		observers.add(o);
	}

	public void removeObserver(Observer o) {
		int i = observers.indexOf(o);
		if (i >= 0) {
			observers.remove(i);
		}
	}

	public void notifyObservers() {
		for (int i = 0; i < observers.size(); i++) {
			Observer observer = (Observer)observers.get(i);
			observer.update(temperature, humidity);
		}
	}

	public void measurementsChanged() {
		notifyObservers();
	}

	public void setMeasurements(float temperature, float humidity) {
		this.temperature = temperature;
		this.humidity = humidity;
		measurementsChanged();
    }
}
```

・実行コード
``` java
public class Client {

	public static void main(String[] args) {
		WeatherData weatherData = new WeatherData();

		CurrentConditionsDisplay currentDisplay = new CurrentConditionsDisplay(weatherData);
		weatherData.setMeasurements(27, 65);
		weatherData.setMeasurements(25, 55);
	}
}

// 実行結果
// 現在の気象状況: 温度27度 湿度65%
// 現在の気象状況: 温度25度 湿度55%
```
