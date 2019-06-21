# VectorDrawable NotFoundException 이슈

## 이슈
`Nexus 4` `android 5.1.1` 기기에서 에러 발생하며 앱 crach 발생

## 로그
```
FATAL EXCEPTION: main
    Process: com.xxxxxx, PID: 5133
    android.view.InflateException: Binary XML file line #51: Error inflating class ImageView
        at android.view.LayoutInflater.createViewFromTag(LayoutInflater.java:763)
        at android.view.LayoutInflater.rInflate(LayoutInflater.java:806)
        at android.view.LayoutInflater.inflate(LayoutInflater.java:504)
        at android.view.LayoutInflater.inflate(LayoutInflater.java:414)
        at com.xxxxxx.adapter.IntroAdapter.instantiateItem(HomeOnBoardingIntroAdapter.kt:17)
        at androidx.viewpager.widget.ViewPager.addNewItem(ViewPager.java:1010)
        at androidx.viewpager.widget.ViewPager.populate(ViewPager.java:1158)
        at androidx.viewpager.widget.ViewPager.populate(ViewPager.java:1092)
        at androidx.viewpager.widget.ViewPager.onMeasure(ViewPager.java:1622)
        at android.view.View.measure(View.java:17547)
        at androidx.constraintlayout.widget.ConstraintLayout.internalMeasureChildren(ConstraintLayout.java:1248)
        at androidx.constraintlayout.widget.ConstraintLayout.onMeasure(ConstraintLayout.java:1593)
        at android.view.View.measure(View.java:17547)
        at android.view.ViewGroup.measureChildWithMargins(ViewGroup.java:5535)
        at android.widget.FrameLayout.onMeasure(FrameLayout.java:436)
        at android.view.View.measure(View.java:17547)
        at androidx.constraintlayout.widget.ConstraintLayout.internalMeasureChildren(ConstraintLayout.java:1248)
        at androidx.constraintlayout.widget.ConstraintLayout.onMeasure(ConstraintLayout.java:1593)
        at android.view.View.measure(View.java:17547)
        at android.view.ViewGroup.measureChildWithMargins(ViewGroup.java:5535)
        at android.widget.FrameLayout.onMeasure(FrameLayout.java:436)
        at androidx.appcompat.widget.ContentFrameLayout.onMeasure(ContentFrameLayout.java:143)
        at android.view.View.measure(View.java:17547)
        at android.view.ViewGroup.measureChildWithMargins(ViewGroup.java:5535)
        at android.widget.FrameLayout.onMeasure(FrameLayout.java:436)
        at android.view.View.measure(View.java:17547)
        at android.view.ViewGroup.measureChildWithMargins(ViewGroup.java:5535)
        at android.widget.FrameLayout.onMeasure(FrameLayout.java:436)
        at android.view.View.measure(View.java:17547)
        at android.view.ViewGroup.measureChildWithMargins(ViewGroup.java:5535)
        at android.widget.LinearLayout.measureChildBeforeLayout(LinearLayout.java:1436)
        at android.widget.LinearLayout.measureVertical(LinearLayout.java:722)
        at android.widget.LinearLayout.onMeasure(LinearLayout.java:613)
        at android.view.View.measure(View.java:17547)
        at android.view.ViewGroup.measureChildWithMargins(ViewGroup.java:5535)
        at android.widget.FrameLayout.onMeasure(FrameLayout.java:436)
        at com.android.internal.policy.impl.PhoneWindow$DecorView.onMeasure(PhoneWindow.java:2615)
        at android.view.View.measure(View.java:17547)
        at android.view.ViewRootImpl.performMeasure(ViewRootImpl.java:2015)
        at android.view.ViewRootImpl.measureHierarchy(ViewRootImpl.java:1173)
        at android.view.ViewRootImpl.performTraversals(ViewRootImpl.java:1379)
        at android.view.ViewRootImpl.doTraversal(ViewRootImpl.java:1061)
        at android.view.ViewRootImpl$TraversalRunnable.run(ViewRootImpl.java:5885)
        at android.view.Choreographer$CallbackRecord.run(Choreographer.java:767)
        at android.view.Choreographer.doCallbacks(Choreographer.java:580)
        at android.view.Choreographer.doFrame(Choreographer.java:550)
        at android.view.Choreographer$FrameDisplayEventReceiver.run(Choreographer.java:753)
        at android.os.Handler.handleCallback(Handler.java:739)
        at android.os.Handler.dispatchMessage(Handler.java:95)
        at android.os.Looper.loop(Looper.java:135)
        at android.app.ActivityThread.main(ActivityThread.java:5254)
        at java.lang.reflect.Method.invoke(Native Method)
        at java.lang.reflect.Method.invoke(Method.java:372)
        at com.android.internal.os.ZygoteInit$MethodAndArgsCaller.run(ZygoteInit.java:903)
        at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:698)
     Caused by: android.content.res.Resources$NotFoundException: File res/drawable/ic_image_gradation.xml from drawable resource ID #0x7f080259
```

## 해결 방법
`android:background` -> `app:srcCompat` 변경하여 이슈 해결

```xml
<ImageView
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:background="@drawable/ic_image_gradation"/>
```
```xml
<ImageView
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:srcCompat="@drawable/ic_image_gradation" />
"/>
```

## 원인
안드로이드 롤리팝 `Android 5.0 (API level 21)` 이하 버전에서 백터 이미지 사용시에는 `app:srcCompat` 사용 해야함

## 참고
- [Difference between app:srcCompat and android:src in Android's layout XML](https://stackoverflow.com/questions/40624554/difference-between-appsrccompat-and-androidsrc-in-androids-layout-xml)
- (https://developer.android.com/studio/write/vector-asset-studio?hl=ko_

