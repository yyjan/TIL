
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

 

# filter
 ```kotlin
inline fun <T> Array<out  T>.filter(
	predicate: (T) -> Boolean
): List<T>
```
- [filter](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/filter.html) 
- 리스트내에 인자들 중 조건에 일치하는 인자만 필터링 할 수 있다.
- ex)  인자들중 널 값을 제거 하고 싶은 경우 `list.filter { it.isNotEmpty() }`
 
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