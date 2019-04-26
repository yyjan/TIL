
# Null Safety
- [Null Safety](https://kotlinlang.org/docs/reference/null-safety.html)
- 코틀린에서는 더 안전하고 편하게 `null`을 처리할 수 있다.
  

## 안전한 호출 (Safe Calls)
```kotlin
val a = "Kotlin"
val b: String? = null

println(b?.length)
println(a?.length) // Unnecessary safe call
```
b `null`이면 return은 `null`이 된다.

```kotlin
bob?.department?.head?.name
```
여러 변수를 중첩으로 호출하게 되었을 때 장점을 가진다.
  

## 엘비스 오퍼레이터 (Elvis Operator)
```kotlin
val l = b?.length ?: -1
```
b가 `null`이 아닌 경우만 호출을 해서 값을 리턴, 그렇지 않은 경우엔 `-1` 을 호출 한다.


## 강제 not null 처리 (The !! Operator)
```kotlin
val l = b!!.length
```
b가 `null` 이면 `NullPointerException` 발생 한다.
  

## Safe Casts
```kotlin
val aInt: Int? = a as? Int
```
`as?` 는 casting을 시도하고, casting 이 불가능 하면 `null`을 반환 한다.
 `ClassCastException` 를 방지 가능 하다.


## Collections of Nullable Type
```kotlin
val nullableList: List<Int?> = listOf(1, 2, null, 4)
val intList: List<Int> = nullableList.filterNotNull()
```
인자들중 `null` 값을 제거 하고 싶은 경우 사용 가능 하다.