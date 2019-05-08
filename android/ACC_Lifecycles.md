# Android Architecture Component - Lifecycles
- Lifecycle-aware components는 Activity, Fragment 등의 lifecycle이 변경되면 이에 반응하여 동작함
- 생명주기의 모니터링을 돕는다

## Lifecycle
![lifecycle-states](https://developer.android.com/images/topic/libraries/architecture/lifecycle-states.png)
- `Lifecycle` 클래스는 Activity 나 fragment의 Lifecycle 상태를 가짐
- 내부에 `Event` `State` 두가지의 enum을 가진다
---
### Event
![LifeCycle events timeline](https://cdn-images-1.medium.com/max/1600/1*RqOdr-NppqAl4elgMY6Qkw.jpeg)
---
### State
![Lifecycle states timeline](https://cdn-images-1.medium.com/max/1600/1*GKpyv8DQ3qJMKvpGWEVIyw.jpeg)
---
```kotlin
if (lifeCycle.currentState.isAtLeast(Lifecycle.State.STARTED)) {
    ...
}
```
- `State.isAtLeast` 로 현재 상태 확인 가능함

## Lifecycle Observer
```kotlin
class MainLifecycleObserver(val lifecycle: Lifecycle) : LifecycleObserver {
    @OnLifecycleEvent(Lifecycle.Event.ON_RESUME)
    fun connectListener() {
        ...
    }

    @OnLifecycleEvent(Lifecycle.Event.ON_PAUSE)
    fun disconnectListener() {
        ...
    }
}
```
- `LifecycleObserver` 상속하여 Observer 구현
- 수명 주기 이벤트를 모니터링 할 수 있는 클래스

## Lifecycle Owner
```kotlin
class MainActivity: AppCompatActivity() {

	override fun onCreate(savedInstanceState: Bundle ? ) {
		super.onCreate(savedInstanceState)
		setContentView(R.layout.activity_main)

		val lifeCycleObserver = MainLifecycleObserver(lifecycle)
		lifecycle.addObserver(lifeCycleObserver)
	}
```
- `LifecycleOwner`는 lifecycle 반환하는 인터페이스
- Lifecycle에 생명주기 메소드를 정의한 `LifecycleObserver`를 등록


## 참고 
- [Handling Lifecycles with Lifecycle-Aware Components](https://developer.android.com/topic/libraries/architecture/lifecycle)
- [Android Architecture Components 소개](https://medium.com/@maryangmin/android-architecture-components-%EC%86%8C%EA%B0%9C-1-8e04491be1f6)
- [Android Architecture Components: LifeCycle](https://medium.com/@MinaSamy/android-architecture-components-lifecycle-433ace1ec05d)