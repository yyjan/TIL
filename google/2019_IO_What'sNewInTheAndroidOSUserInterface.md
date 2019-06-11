# What’s New in Android (Google I/O’19)
What's New in the Android OS User Interface 세션 

## Sharing
### 안드로이드 Q 개선사항
- 훨씬 향상된 성능
- 단순하고 진보된 UI
- 추가 개발자 사용자 설정

### Sharing shortcuts
![2019_io_sharing_shortcuts_1](https://github.com/yyjan/TIL/blob/master/images/2019_io_sharing_shortcuts_1.png)
![2019_io_sharing_shortcuts_2](https://github.com/yyjan/TIL/blob/master/images/2019_io_sharing_shortcuts_2.png)
- 앱에 있는 content를 빠르게 공유할 수 있는 기능
- 사용자가 앱 내에서 더 많은 정보를 직접 공유할 수 있게함
- 구현 Activity는 AndroidManifest에 ACTION_SEND Intent Filter 필요

### Add a rich content preview 
![2019_io_sharing_preview_1](https://github.com/yyjan/TIL/blob/master/images/2019_io_sharing_preview_1.png)
![2019_io_sharing_preview_2](https://github.com/yyjan/TIL/blob/master/images/2019_io_sharing_preview_2.png)
- 유저가 공유한 Content에 관한 Preview 제공

### Add custom target
![2019_io_sharing_custom_target](https://github.com/yyjan/TIL/blob/master/images/2019_io_sharing_custom_target.png)
- Target, Intent 설정을 추가 가능

## Notification
### Gentle notifications
![2019_io_notifications_actions](https://github.com/yyjan/TIL/blob/master/images/2019_io_notifications_actions.png)

### Notifications actions
![2019_io_notifications_gentle](https://github.com/yyjan/TIL/blob/master/images/2019_io_notifications_gentle.png)
- 모든 메세징 알림에서 기본적으로 사용됨 
- 메세지 답장을 수신 받은 Content와 관련 있는 내용으로 답장 가능
- (URL, 주소, 이메일, 앱 딥 링크 및 코드)

## MultiTasking
### Bubbles
![2019_io_bubbles_1](https://github.com/yyjan/TIL/blob/master/images/2019_io_bubbles_1.png)
- 유저의 멀티 태스킹을 위한 API
- Bubbles Notification 클락으로 다른 작업을 완료하고 빠르게 이전 작업으로 돌아 갈 수 있음

![2019_io_bubbles_2](https://github.com/yyjan/TIL/blob/master/images/2019_io_bubbles_2.png)
- Bubble의 2가지 상태
- `Collapsed`: 마지막 상태 post 
- `Expanded`: 해당 내용의 Activity content를 보여줌

- [bubbles API 문서](https://developer.android.com/preview/features/bubbles)

## 참고
- [What's New in the Android OS User Interface (Google I/O'19)](https://www.youtube.com/watch?v=nWbW58RMteI)