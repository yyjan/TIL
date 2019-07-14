# ConstraintLayout

## Guideline
```xml
<android.support.constraint.ConstraintLayout
        xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        xmlns:tools="http://schemas.android.com/tools"
        android:layout_width="match_parent"
        android:layout_height="match_parent">

    <android.support.constraint.Guideline
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:id="@+id/guideline"
            app:layout_constraintGuide_begin="100dp"
            android:orientation="vertical"/>

    <Button
            android:text="Button"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:id="@+id/button"
            app:layout_constraintLeft_toLeftOf="@+id/guideline"
            android:layout_marginTop="16dp"
            app:layout_constraintTop_toTopOf="parent" />
</android.support.constraint.ConstraintLayout>
```
- 뷰의 위치를 잡는데 도움을 주는 유틸리티 클래스
- `layout_constraintGuide_begin`: 좌측 또는 상단으로부터 고정된 거리값으로 배치
- `layout_constraintGuide_end` : 우측 또는 하단으로부터 고정된 거리값으로 배치
- `layout_constraintGuide_percent` : 0부터 1까지 float값을 넣어 전체 길이의 비례적으로 배치 

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

## Gone Margin
연결되었던 뷰의 가시성(Visibility)이 숨김상태(GONE)일 때에 대한 여백을 따로 적용하고 싶을때 사용
- `layout_goneMarginStart`
- `layout_goneMarginEnd`
- `layout_goneMarginLeft`
- `layout_goneMarginTop`
- `layout_goneMarginRight`
- `layout_goneMarginBottom`

## 참고
- [ConstraintLayout](https://developer.android.com/reference/android/support/constraint/ConstraintLayout)
- [ConstraintLayout과 함께 안드로이드 앱 편하게 개발하기](https://academy.realm.io/kr/posts/cool-constraintlayout-droidcon-boston-2017/)
- [Constraint Layout – Part1. 만능 레이아웃](https://www.charlezz.com/?p=669)
- [Android ConstraintLayout 쉽게 알아가자](https://medium.com/@futureofdev/android-constraintlayout-%EC%89%BD%EA%B2%8C-%EC%95%8C%EC%95%84%EA%B0%80%EC%9E%90-62d2ded79c17)
- [안드로이드 ConstraintLayout 구현 방법](https://codechacha.com/ko/constraintlayout/)
- [Guideline reference](https://developer.android.com/reference/android/support/constraint/Guideline)
- [guidelines](https://constraintlayout.com/basics/guidelines.html)