# Android resource naming convention 
- 코드를 명확하고 사용하기 쉽게 만들기 위해서 참고하면 좋을듯 하다
  
## Layouts
```xml
<WHAT>_<WHERE>.XML
```

- activity_main: view for the ArticleDetailFragment
- fragment_articledetail: layout inflated by custom view class MenuView
- view_menu: layout inflated by custom view class MenuView
- item_article: list item in ArticleRecyclerView
- layout_actionbar_backbutton: layout for an actionbar with a backbutton (too simple to be a customview)

 
## Strings
```xml
<WHERE>_<DESCRIPTION> or <HOW>_<DESCRIPTION>
```
- articledetail_title: title of ArticleDetailFragment
- feedback_namehint: hint of name field in FeedbackFragment
- label_home: label & home is description of the string
- hint_user_name: how = hint & user_name is the description of string

 
```xml
all_<DESCRIPTION>
```
- all_done: generic “done” string

  
## Drawables
```xml
<WHERE>_<DESCRIPTION>_<SIZE> or <WHAT>_<DESCRIPTION>
```
- articledetail_placeholder: placeholder in ArticleDetailFragment
- ab_stacked_9: Acrion bar
- btn_send_pressed_9: Button
- divider_hotizontal_9: divider

```xml
all_<DESCRIPTION>_<SIZE>
```
- all_infoicon: generic info icon
- all_infoicon_24dp: 24dp version of generic info icon
  

## Dimensions
```xml
<WHAT>_<WHERE>_<SIZE>
```
- `<WHAT>` : It can be width(in dp), height (in dp), size (if width == height), margin(in dp), padding(in dp), elevation(in dp). text_size(in sp)
- size_menu_icon
- height_toolbar
- height_menu_profileimage


## 참고
-  [Android resource naming convention](https://medium.com/mindorks/android-resource-naming-convention-42e4e8026614)
-  [A successful XML naming convention](https://jeroenmols.com/blog/2016/03/07/resourcenaming/)