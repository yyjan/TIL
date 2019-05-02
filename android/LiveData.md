# Android Architecture Component - LiveData
- Data의 변경을 관측할 수 있는 data holder 클래스
- 일반적인 Observable과 다르게 LiveData는 생명주기를 알고 있음 (Lifecycle-Aware)
- 활성 상태 (STARTED, RESUMED) 경우에만 데이터를 업데이트


## LiveData 사용시 장점
#### Data와 UI간 동기화
앱의 데이터가 변할때마다 매번 UI를 갱신하는 대신, 옵저버에 변화가 감지될 때마다 UI를 갱신하도록 통합시킬 수 있다.

#### Memory leak 방지
Observer들이 Lifecycle 객체와 바인드되고, Lifecycle 객체가 destroy 상태가 되면 자동적으로 cleanup 된다.

#### 액티비티가 종료됨으로 인한 Crash 방지
엑티비티가 백스택에 있을때와 같이, 옵저버의 생명주기가 비활성화 상태일 때는, LiveData 이벤트도 받지 않는다.

#### 직접 생명주기를 핸들링할 필요가 없다
UI 컴포넌트는 단지 연관된 데이터를 관찰(Observe)하기만 하고, onStop ,onResume 에서 해제, 등록 하는 절차를 할필요가 없다.
LiveData가 상태변화를 감지하여 알아서 관리해준다.

#### 항상 최신 데이터를 유지한다
생명주기가 비활성화 상태에서 활성화 상태로 변했을 때, UI 컴포넌트는 최신의 데이터를 받는다. 
ex) 백그라운드의 엑티비티가 > 포그라운드, 최신의 데이터 받음

#### 구성(Configuration)이 변경되었을 때 적절하게 대응한다
Activity나 Fragment가 구성변경되어 재생성될 때, 그 컴포넌트들은 LiveData로부터 즉시 최신데이터를 제공받는다.
ex) 가로-세로 화면전환, 재생성(recreated) 되어도 최신의 데이터 받음

#### 자원 공유
싱글턴 패턴을 이용해 시스템 서비스를 래핑(wrap)하여 LiveData 객체가 공유될 수 있도록 확장할 수 있다. 앱 어디에서나 공유가 가능하다.


## LiveData 생성 
```kotlin
class MainViewModel : ViewModel() {
    private val _data = MutableLiveData<String>()

    val data: MutableLiveData<String>
        get() = _data

    init {
        _data.value = "LiveData test"
    }
}
```

## LiveData data 변경 관측
```kotlin
override fun onActivityCreated(savedInstanceState: Bundle?) {
    super.onActivityCreated(savedInstanceState)
    viewModel = ViewModelProviders.of(this).ge(MainViewModel::class.java)
    viewModel.data.observe(this, Observer { data ->
        tv_message.text = data
    })

    btn_click.setOnClickListener {
        viewModel.data.value = "button clicked"
    }

}
```

## LiveData data 변경
```kotlin
btn_click.setOnClickListener {
        viewModel.data.value = "button clicked"
    }
```      

## 참고
- [LiveData Overview](https://developer.android.com/topic/libraries/architecture/livedata.html)
- [Android Architecture Component – LiveData](https://www.charlezz.com/?p=363)
- [Architecture Component 2 - LiveData 공식문서 번역](http://dktfrmaster.blogspot.com/2018/02/livedata.html)
