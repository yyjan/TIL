
# joinToString
```kotlin
fun <T> Array<out T>.joinToString(
	separator: CharSequence = ", ",
	prefix: CharSequence = "",
	postfix: CharSequence = "",
	limit: Int = -1,
	truncated: CharSequence = "...",
	transform: (T) -> CharSequence = null
): String
```

- [joinToString](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/join-to-string.html#jointostring) 
- 구분자 추가가 필요한 경우에 경우 유용하게 사용이 가능하다.
- ex) `#태그1 #태그2 #태그3` 과 같이 공백을 넣을 수 있다.
  
## 예제
```kotlin
val numbers = listOf(1, 2, 3, 4, 5, 6)

println(numbers.joinToString()) // 1, 2, 3, 4, 5, 6
println(numbers.joinToString(prefix = "[", postfix = "]")) // [1, 2, 3, 4, 5, 6]
println(numbers.joinToString(prefix = "<", postfix = ">", separator = "•")) // <1•2•3•4•5•6>
 
val chars = charArrayOf('a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q')

println(chars.joinToString(limit = 5, truncated = "...!") { it.toUpperCase().toString() }) // A, B, C, D, E, ...! 
```
<br>
<br>

# filter
 ```kotlin
inline fun <T> Array<out  T>.filter(
	predicate: (T) -> Boolean
): List<T>
```
- [filter](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/filter.html) 
- 리스트내에 인자들 중 조건에 일치하는 인자만 필터링 할 수 있다.
- ex) 인자들중 "" 값을 제거 하고 싶은 경우 `list.filter { it.isNotEmpty() }`
- ex) 인자들중 null 값을 제거 하고 싶은 경우 `list.filterNotNull()`
 
## 예제
```kotlin
val originalMap = mapOf("key1" to 1, "key2" to 2, "key3" to 3)
val filteredMap = originalMap.filter { it.value < 2 }

println(filteredMap) // {key1=1}
// original map has not changed
println(originalMap) // {key1=1, key2=2, key3=3}
  
val nonMatchingPredicate: ((Map.Entry<String, Int>)) -> Boolean = { it.value == 0 }
val emptyMap = originalMap.filter(nonMatchingPredicate)

println(emptyMap) // {}
```
<br>
<br>

# first(), last() 
 ```kotlin
class Test {
    val animals = listOf("A", "B", "C")

    fun first() {
        animals.first().forEach { println(it) }
        animals.firstOrNull()?.forEach { println(it) }

        animals.last().forEach { println(it) }
        animals.lastOrNull()?.forEach { println(it) }
    }
}
 ```
- [first](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/first.html) 
- [last](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/last.html) 
- `first()` 첫번째 아이템 반환, 아이템이 존재 하지 않는다면 `NoSuchElementException` 발생
- `firstOrNull` 첫번째 아이템 반환, 아이템이 존재 하지 않는다면 'Null' 반환

# drop
- [drop](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/drop.html)
```kotlin
val chars = ('a'..'z').toList()
println(chars.drop(2)) 
// [c, d, e, f, g, h, i, j, k, l, m, n, o, p, q, r, s, t, u, v, w, x, y, z]

println(chars.dropLast(2))
// [a, b, c, d, e, f, g, h, i, j, k, l, m, n, o, p, q, r, s, t, u, v, w, x]

println(chars.dropWhile { it < 'x' }) // [x, y, z]
// [x, y, z]

println(chars.dropLastWhile { it > 'c' }) // [a, b, c]
// [a, b, c]
 ```

## 참고
- [Package kotlin.collections](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/index.html)
- [코틀린 스트림 함수](https://namget.tistory.com/entry/Kotlin-%EC%BD%94%ED%8B%80%EB%A6%B0-%EC%8A%A4%ED%8A%B8%EB%A6%BC-%ED%95%A8%EC%88%98-map-flatMap-groupBy-filter-take-drop-first-distinct-zip-joinToString-count-any-none-max-min-average)