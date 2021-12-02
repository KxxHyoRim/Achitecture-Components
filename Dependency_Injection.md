# DI(Dependency Injection)



## DI(Dependency Injection)란?

단일클래스로 개발을 할 수 없기 때문에 클래스간의 참조는 필수적으로 일어난다. ex) Car-Engine

Car이라는 클래스가 실행되기 위해서는 Engine이라는 클래스의 인스턴스가 있어야 한다.



참조 방법은 크게 3가지가 있고, 그 중에 하나가 DI이다.

1. 클래스가 필요한 종속 항목을 구성합니다.

   위의 예에서 `Car`는 자체 `Engine` 인스턴스를 생성하여 초기화합니다.

2. 다른 곳에서 객체를 가져옵니다. `Context` getter 및 `getSystemService()`와 같은 일부 Android API는 이러한 방식으로 작동합니다.

3. 객체를 매개변수로 제공받습니다. 앱은 클래스가 구성될 때 이러한 종속 항목을 제공하거나 각 종속 항목이 필요한 함수에 전달할 수 있습니다. 위의 예에서 `Car` 생성자는 `Engine`을 매개변수로 받습니다.



### 1.  자체 `Engine` 종속 항목을 생성하는 `Car`

```kotlin
class Car {

    private val engine = Engine()

    fun start() {
        engine.start()
    }
}

fun main(args: Array) {
    val car = Car()
    car.start()
}
```

- Gas 및 Electric 유형의 엔진에 동일한 Car를 재사용하는 대신 두가지 유형의 `Car`를 생성해야한다.

- Car는 Engine에 강하게 종속되어 있으므로, Car만 따로 분리하여 테스팅하는 것이 어려움.



### 2. Car 내부에서 getEngine을 통해 Engine을 가져옴

(다른 곳에 저장되어 있는 객체를 가져옴)

```kotlin
class Car(private val engine: Engine) {
    fun start() {
        engine.start()
    }
}

fun main(args: Array) {
    val engine = Engine()
    val car = Car(engine)
    car.start()
}
```

