# lateinit
- [lateinit](https://kotlinlang.org/docs/reference/null-safety.html)
- var(mutable) 프로퍼티만 사용 가능
- 커스텀 getter/setter가 없는 프로퍼티만 사용 가능
- 로컬 변수로 사용 불가능

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
