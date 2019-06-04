# What's New in Architecture Components (Google I/O’19)
Google I/O 2019 What's New in Architecture Components 세션 

## Data Binding
- `Android Studio 3.5 베타` 기준 성능향상, Incremental annotation processing 위한 옵션
- 20% 더 빠른 주석 처리
- 분산된 빌드 캐시 지원
- 증분 주석 처리 : `android.databinding.incremental = true`

## Android Studio 3.5
![2019_io_androidstudio_1](https://github.com/yyjan/TIL/blob/master/images/2019_io_androidstudio_1.png)
- Live Class Generation 가능 (항상 리빌드 필요 > 실시간 처리)
- Rebuild로 인해 생기는 대기시간을 최소화

![2019_io_androidstudio_2](https://github.com/yyjan/TIL/blob/master/images/2019_io_androidstudio_2.png)
- Refactoring 지원 (Code에서 변수 이름을 Rename을 통해서 변경하면 즉시 반영)

![2019_io_androidstudio_3](https://github.com/yyjan/TIL/blob/master/images/2019_io_androidstudio_3.png)
- Data Binding 컴파일 오류 확인 가능

## View Binding
![2019_io_viewbinding](https://github.com/yyjan/TIL/blob/master/images/2019_io_viewbinding.png)
- 아름다운 코드 적용, 컴파일 타임 안전성 확보, 빌드 속도 향상
- Android Studio 3.6 버전부터 제공

## ViewModel
```kotlin
val vm = ViewModelProvider(this, SavedStateVMFactory(this))
        .get(SavedStateViewModel::class.java)
```
- [SavedState](https://developer.android.com/topic/libraries/architecture/viewmodel-savedstate) 추가 지원 

```kotlin
// 기존 방법
ViewModelProviders.of(this).get(MyViewModel::class.java)

// 신규 방법
val myViewModel: MyViewModel by viewModels()
```
- ViewModel 초기화 코드를 간결하게 사용 가능

## WorkManager
![2019_io_workmanager_1](https://github.com/yyjan/TIL/blob/master/images/2019_io_workmanager_1.png)
![2019_io_workmanager_2](https://github.com/yyjan/TIL/blob/master/images/2019_io_workmanager_2.png)
- 활용 방법이 변경됨
- alpha 버전에서 Worker에 대한 unit test가 가능해진다.

## Room 
- `Room 2.1` 변경 정보
```kotlin
@Dao
interface SongDao {
  @Query("""
    SELECT *
    FROM Song
    WHERE Song MATCH :query
  """)
  fun searchSongs(query: String): List<Song>
}
```

- 별도의 쿼리 대신 data class 직접 사용 가능

```kotlin
@DatabaseView("SELECT user.id, user.name, user.departmentId," +
        "department.name AS departmentName FROM user " +
        "INNER JOIN department ON user.departmentId = department.id")
data class UserDetail(
    val id: Long,
    val name: String?,
    val departmentId: Long,
    val departmentName: String?
)
```
```kotlin
@Database(entities = arrayOf(User::class),
          views = arrayOf(UserDetail::class), version = 1)
abstract class AppDatabase : RoomDatabase() {
    abstract fun userDao(): UserDao
}
```
- [Database views](https://developer.android.com/training/data-storage/room/creating-views#kotlin) 제공


## 참고
- [What's New in Architecture Components (Google I/O'19)](https://www.youtube.com/watch?v=Qxj2eBmXLHg)
- [2019 Google IO - Architecture Components 정리](https://thdev.tech/google%20io/2019/05/10/Google-IO-2019-Architecture-Components)