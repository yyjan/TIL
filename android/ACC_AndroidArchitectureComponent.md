# Android Architecture Component
안드로이드는 Activity, BroadcastReceiver, Service, ContentProvider 등 여러 컴포넌트들이 있고, 생명주기가 다르게 얽혀있다.
앱을 잘 만들기 위해서는 이러한 컴포넌트들을 부드럽게 연결해야 하는데, 생명주기를 학습하고 엉키지 않도록 고민하는 어려움이 있어, 구글은 SDK에서 제공하는 컴포넌트들에 대해 개발자들에게 가이드 제공하기로 함

## AAC 구성
1. Lifecycles (Easy handling lifecycles)
2. LiveData (Lifecycle aware observable)
3. ViewModel (Managing data in a lifecycle)
4. Room (Object Mapping for SQLite)
5. Paging (Gradually loading information)
Google I/O 2017에 발표한 4가지와 추후에 추가된 1개까지 총 5개의 라이브러리로 구성

![Android Architecture](https://cdn-images-1.medium.com/max/1600/1*okKV5_-dxVTcYzqjaUtCtw.jpeg)
1. Activity / Fragment
- `View` 계층을 의미한다.
- 비지니스 로직과 복합한 operation 을 처리하지 않는다.
- 오직 UI 를 다루고, `ViewModel` 로 부터 `LiveData` 를 관찰하고 표시한다.

2. ViewModel
- `View` 의 `Lifecycle` 상태를 자동으로 관찰한다.
- `Repository` 로 부터 data를 가져온다
- 결코 View 를 직접적으로 참조하지 않고, data 업데이는 `LiveData` 에 의한 것

3. Repository 
- 특정적인 구현 없이 간단한 클래스로, database 에서 data를 가져오는 역할을 한다.
- 모든 데이터를 처리하여 관찰가능한 `LiveData` 로 변환 > `ViewModel` 에서 사용할 수 있도록 만든다.

4. Room
- SQLite 매핑 라이브러리, database 프로세스 처리를 쉽게 한다.
- 관찰가능한 `LiveData` 가 있는 쿼리를 직접 return 할 수 있다.


## 참고 
- [Android Architecture Components](https://developer.android.com/topic/libraries/architecture)
- [Introduction to Android Architecture Components](https://code.tutsplus.com/tutorials/introduction-to-android-architecture--cms-28749?_ga=2.135099573.569241047.1556851538-1107741534.1556851538)
- [번역/Android Architecture Components 소개](https://medium.com/@futureofdev/android-architecture-components%EB%A5%BC-%EC%86%8C%EA%B0%9C%ED%95%A9%EB%8B%88%EB%8B%A4-1-5a142eeb332f)
- [Android Architecture Components 소개](https://medium.com/@maryangmin/android-architecture-components-%EC%86%8C%EA%B0%9C-1-8e04491be1f6)
