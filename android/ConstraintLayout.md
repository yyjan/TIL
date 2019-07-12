# ConstraintLayout

## Ratio 비율 적용 
```xml
<Button android:layout_width="wrap_content"
        android:layout_height="0dp" 
        app:layout_constraintDimensionRatio="1:1" />
```
- `android:layout_width="wrap_content"` 가로 사이즈 기준
- `수평:수직` 1:1

```xml
<Button android:layout_width="0dp"
        android:layout_height="0dp"
        app:layout_constraintDimensionRatio="H,16:9"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintTop_toTopOf="parent"/>
```
- `android:layout_width="0dp"` `android:layout_height="0dp"` 가로 세로 둘다 비율 적용
- `W` 수평, `H` 수직, 16:9

## 중앙 배치
- `layout_constraintHorizontal_bias` : 가로축에서 객체의 치우친 정도를 설정
- `layout_constraintVertical_bias` : 세로축에서 객체의 치우친 정도를 설정
```xml
<TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintHorizontal_bias="0.2"/>
```
- `layout_constraintHorizontal_bias="0.2"` 객체 왼쪽의 여백 20%, 오른쪽 80%

## 참고
- [ConstraintLayout](https://developer.android.com/reference/android/support/constraint/ConstraintLayout)
- [ConstraintLayout과 함께 안드로이드 앱 편하게 개발하기](https://academy.realm.io/kr/posts/cool-constraintlayout-droidcon-boston-2017/)
- [Constraint Layout – Part1. 만능 레이아웃](https://www.charlezz.com/?p=669)
- [Android ConstraintLayout 쉽게 알아가자](https://medium.com/@futureofdev/android-constraintlayout-%EC%89%BD%EA%B2%8C-%EC%95%8C%EC%95%84%EA%B0%80%EC%9E%90-62d2ded79c17)
- [안드로이드 ConstraintLayout 구현 방법](https://codechacha.com/ko/constraintlayout/)