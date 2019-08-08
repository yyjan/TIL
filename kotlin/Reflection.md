# Reflection
- 코틀린에서 더블콜론 `::` 은 리플렉션을 위해 사용
- 런타임시에 내가 작성한 코드가 어디에 위치하는지 알 수 없기 때문에 바이트코드를 이용해 내가 참조하려는 값을 찾기위해 사용
- 반사, 투영 의미

## Class 참조
```kotlin
val c = MyClass::class
```

## Function 참조
```kotlin
fun isOdd(x: Int) = x % 2 != 0
fun isOdd(s: String) = s == "brillig" || s == "slithy" || s == "tove"

val numbers = listOf(1, 2, 3)
println(numbers.filter(::isOdd)) // refers to isOdd(x: Int)

// [1, 3]
```

## Property 참조 
```kotlin
private lateinit var sampleAdapter: SampleAdapter

if (::sampleAdapter.isInitialized) {
        ....
    }
```

## 참고
- [Reflection](https://kotlinlang.org/docs/reference/reflection.html)
- [코틀린의 더블콜론(::) 참조](https://medium.com/harrythegreat/%EC%BD%94%ED%8B%80%EB%A6%B0%EC%9D%98-%EB%8D%94%EB%B8%94%EC%BD%9C%EB%A1%A0-%EC%B0%B8%EC%A1%B0-73ff25484586)