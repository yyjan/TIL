# toUpperCase
```kotlin
val chars = listOf('a', 'ω', '1', 'A', '+')
val upperCases = chars.map { it.toUpperCase() }
println(upperCases) // [A, Ω, 1, A, +]
```
- 문자열을 모두 대문자로 변경

# toLowerCase
```kotlin
val chars = listOf('A', 'Ω', '1', 'a', '+')
val lowerCases = chars.map { it.toLowerCase() }
println(lowerCases) // [a, ω, 1, a, +]
```
- 문자열을 모두 소문자로 변경

## 참고
- [toUpperCase](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.text/to-upper-case.html?q=&p=0)
- [toLowerCase](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.text/to-lower-case.html)
