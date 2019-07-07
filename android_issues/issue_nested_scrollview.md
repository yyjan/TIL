# NestedScrollView 안의 버튼을 두번 클릭해야 작동하는 이슈

## 이슈
- `NestedScrollView` 안에 `Button` 을 눌러서 기능을 실행할때 두번을 눌러야 실행됨
- 내용이 짧아서 스크롤이 필요없이 모든 view 가 보인다면 두번 누를 필요없이 바로 실행
- 내용이 길어져서 Button이 스크롤해야 보이게 되는 경우, 무조건 두번을 눌러야 작동됨

## 해결 3가지 방법
1. `NestedScrollView` -> `ScrollView` 변경하여 이슈 해결
2. `onInterceptTouchEvent` 제어로 해결
```java
public class NestedScrollViewClickFixed extends FrameLayout implements NestedScrollingParent, NestedScrollingChild2, ScrollingView {
    @Override
    public boolean onInterceptTouchEvent(MotionEvent ev) {
        switch (action & MotionEvent.ACTION_MASK) {
            case MotionEvent.ACTION_DOWN: {
                // Remove the old write of mIsBeingDragged
                // mIsBeingDragged = !mScroller.isFinished();
                // Force false instead
                mIsBeingDragged = false;
            }
        }
    }
}
```
3. `Custom behavior` 만든 후 `AppBarLayout`의 Behavior 적용하여 해결
```xml
<android.support.design.widget.AppBarLayout
        android:id="@+id/app_bar"
        android:layout_height="..."
        android:layout_width="..."
        app:layout_behavior="your.package.FixAppBarLayoutBehavior">
```
- [FixAppBarLayoutBehavior.java](https://gist.github.com/chrisbanes/8391b5adb9ee42180893300850ed02f2)

## 참고
- [NestedScrollView에서 버튼을 두번 클릭해야 작동하는 경우 해결방법](https://bateaux.tistory.com/4)
- [onClick method not working properly after NestedScrollView scrolled](https://stackoverflow.com/questions/31829976/onclick-method-not-working-properly-after-nestedscrollview-scrolled)
- [Android NestedScrollView children require double click after scroll](https://rileymacdonald.ca/2018/08/06/android-nestedscrollview-children-require-double-click-scroll/)
