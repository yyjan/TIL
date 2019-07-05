# Android Architecture Component - Databinding 
- Android Jetpack의 일부인 데이터 결합 라이브러리
- 프로그래매틱 방식이 아니라 선언적 형식으로 레이아웃의 UI 구성요소를 앱의 데이터 소스와 결합할 수 있는 지원 라이브러리

## Expression language
- [Common features](https://developer.android.com/topic/libraries/data-binding/expressions?hl=ko#common_features)
- Mathematical + - / * %
- String concatenation +
- Logical && ||
- Binary & | ^
- Unary + - ! ~
- Shift >> >>> <<
- Comparison == > < >= <= (Note that < needs to be escaped as &lt;)
- instanceof
- Grouping ()
- Literals - character, String, numeric, null
- Cast
- Method calls
- Field access
- Array access []
- Ternary operator ?:

```xml
android:text="@{String.valueOf(index + 1)}"
android:visibility="@{age > 13 ? View.GONE : View.VISIBLE}"
android:transitionName='@{"image_" + id}'
```

### Null coalescing operator
```xml
android:text="@{user.displayName ?? user.lastName}"
```

## String Format 적용
```xml
<TextView
        android:id="@+id/tv_likes"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@{@string/post_likes(post.likes.size())}"/>
```
```xml
    <string name="post_likes">%d likes</string>
```
- [Android DataBinding String Format 적용하기](https://gogorchg.tistory.com/entry/AndroidDataBinding-String-Format-%EC%A0%81%EC%9A%A9%ED%95%98%EA%B8%B0)

## 참고
- [데이터 바인딩 라이브러리](https://developer.android.com/topic/libraries/data-binding/?hl=ko)
- [MVVM AAC Databinding 사용법](https://medium.com/@gus0000123/android-databinding-%EC%82%AC%EC%9A%A9%EB%B2%95-9a3480a3bfc7)
