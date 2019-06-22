# NestedScrollView vs ScrollView
- 두가지 비교, 자주 쓰는 속성 정리

## NestedScrollView
```
NestedScrollView is just like ScrollView, but it supports acting as both a nested scrolling parent and child on both new and old versions of Android. Nested scrolling is enabled by default.
```
https://developer.android.com/reference/android/support/v4/widget/NestedScrollView.html

## ScrollView
```
A view group that allows the view hierarchy placed within it to be scrolled. 
Scroll view may have only one direct child placed within it. 
To add multiple views within the scroll view, make the direct child you add a view group, for example LinearLayout, and place additional views within that LinearLayout.
```
```
Never add a RecyclerView or ListView to a scroll view. 
Doing so results in poor user interface performance and a poor user experience.

For vertical scrolling, consider NestedScrollView instead of scroll view which offers greater user interface flexibility and support for the material design scrolling patterns.
```
https://developer.android.com/reference/android/widget/ScrollView.html

## 자주 사용하는 attributes
- `android:fillViewport`: ScrollView 하단에 뷰를 붙일 때 필요함
- `android:overScrollMode="never"`: 더이상 스크롤 되지 않을때 나타나는 효과 제거

## 참고
- [Android: ScrollView vs NestedScrollView](https://stackoverflow.com/questions/34773982/android-scrollview-vs-nestedscrollview)
