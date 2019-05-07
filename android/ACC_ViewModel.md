# ViewModel
- 액티비티와 프래그먼트에서 사용되는 UI 관련 데이터를 보관하고, 관리하기 위해 디자인
- 화면 회전시 데이터 유지
- Activity/Fragment에 따라서 ViewModel 유지
- 내부에서 Lifecycle을 사용할 수 있도록 초기화하고 있으며, onDestroy() 동작 시 ViewModel 내부의 onCleared() 호출을 통해 Release를 유도함


## The lifecycle of a ViewModel
![viewmodel-lifecycle](https://developer.android.com/images/topic/libraries/architecture/viewmodel-lifecycle.png)
- 보통 ViewModel 인스턴스는 액티비티의 `onCreate()`에서 요청을 하는데, 액티비티의 `onCreate()`가 여러번 호출되는 상황에서도 `ViewModel Scope` 는 일관되게 유지됨
- 액티비티 스코프가 완전이 종료되는 시점에 종료되고 `onCleared()` 함수 호출


## Implement a ViewModel
```kotlin
class MainViewModel : ViewModel() {
    ...
}
```
- 상속하여 ViewModel 생성 가능

```kotlin
    override fun onCreateView(
        inflater: LayoutInflater, container: ViewGroup?, savedInstanceState: Bundle?
    ): View {

        // Obtain the ViewModel component.
        val viewModel = ViewModelProviders.of(this).get(MainViewModel::class.java)
        viewModel.data.observe(this, Observer { data ->
           ...
        })
    }
```
- `ViewModelProviders.of()` 로 초기화 진행


## ViewModelFactory
```kotlin
class MainViewModel(val repository: Repository) : ViewModel() {
   ...
}
```
```kotlin
class MainViewModelFactory(val repository : Repository) : ViewModelProvider.Factory {
    override fun <T : ViewModel?> create(modelClass: Class<T>): T {
        return MainViewModel(repository) as T
    }
}
```
```kotlin
val viewModel = ViewModelProviders.of(this, MainViewModelFactory(repository)).get(MainViewModel::class.java)
```
- 커스텀 생성자를 갖는 `ViewModel`은 `ViewModelProvider.Factory` 인터페이스를 사용하여 구현함


## 주의점
- `ViewModel` 에 액티비티, 프래그먼트, 뷰에 대한 `context`를 저장하면 안됨
- 액티비티가 재생성 될때, `ViewModel`은 액티비티 수명주기 외부에 존재하기 때문에 UI context를 저장하면 메모리 릭을 발생시킬수 있음
- `ViewModel` 에 액티비티, 프래그먼트, 뷰에 대한 context를 저장하면 안됨
- `Application context`는 전체 앱의 수명주기를 의미하기 떄문에 가능 > (AndroidViewModel 제공)


## AndroidViewModel
```kotlin
class MainViewModel(application: Application, val repository: Repository) : AndroidViewModel(application) {
    ...
}
```
- `ViewModel` 을 상속받고 있으며, `Application` 을 함께 초기화,  context 사용 가능함

## 참고
- [ViewModel Overview](https://developer.android.com/topic/libraries/architecture/viewmodel)
- [Android Architecture Components ViewModel을 간단하게 초기화 하려면?](https://thdev.tech/androiddev/2018/08/05/Android-Architecture-Components-ViewModel-Inject/)
- [안드로이드 아키텍처 컴포넌트, ViewModel 이해하기](https://medium.com/@jungil.han/%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8-viewmodel-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-2e4d136d28d2)