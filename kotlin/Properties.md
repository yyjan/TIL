# lateinit
- [lateinit](https://kotlinlang.org/docs/reference/null-safety.html)
- var(mutable) 프로퍼티만 사용 가능
- 커스텀 getter/setter가 없는 프로퍼티만 사용 가능
- 로컬 변수로 사용 불가능

## lateinit 초기화 확인
- [Checking whether a lateinit var is initialized](https://kotlinlang.org/docs/reference/properties.html#checking-whether-a-lateinit-var-is-initialized-since-12)
- 실제 값을 사용할 때 lateinit을 한번 체크해줌으로써 안전하게 접근 가능

```kotlin
class SampleActivity {

	private lateinit var sampleAdapter: SampleAdapter

	override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)
    setContentView(R.layout.activity_sample_main)

    // 부르는 시점 초기화
    sampleAdapter = SampleAdapter(ImageLoaderAdapterViewModel(this@SampleMainActivity, 3))

		if (::sampleAdapter.isInitialized) {
			sampleAdapter.addItem()
			sampleAdapter.notifyDataSetChanged()
		}
	}
}
```

# lazy
- [lazy](https://kotlinlang.org/docs/reference/delegated-properties.html#lazy)
- val(immutable) 프로퍼티만 사용 가능
- val 이므로 값 교체 불가능
- 커스텀 getter/setter가 없는 프로퍼티만 사용 가능
- 로컬 변수에서 사용 가능
- 호출 시점, 즉 실제 사용되는 시점에 by lazy 정의에 의해서 초기화를 진행
- lazy을 사용하는 경우 기본 Synchronized로 동작

## 예제
```kotlin
public class Example{
  val name: String by lazy { “Amit Shekhar” }
}
```
```kotlin
private val adapter by lazy { RepoAdapter(this) }
```

```kotlin
private val _quests: LiveData<PagedList<Channel>> by lazy { fetchPicks() }
val quests: LiveData<PagedList<Channel>>
    get() = _quests

private fun fetchPicks(): LiveData<PagedList<Channel>> {
      dataSourceFactory?.clear()
      val config = PagedList.Config.Builder()
          .setEnablePlaceholders(false)
          .setInitialLoadSizeHint(QuestListDataSource.PAGE_SIZE)
          .setPageSize(QuestListDataSource.PAGE_SIZE)
          .build()

      dataSourceFactory = QuestDataSourceFactory(
          categoryId,
          pickType,
          channelRepository,
          createObservableTransformer()
      )

      return LivePagedListBuilder(dataSourceFactory!!, config).build()
  }
```

## 참고
- [Kotlin lazy property - lateinit/lazy 살펴보기](https://thdev.tech/kotlin/2018/03/25/Kotlin-lateinit-lazy/)