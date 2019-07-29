# notifyItemChanged()의 payload
```
onBindViewHolder(RecyclerView.ViewHolder holder, int position, List<Object> payloads)
```
- Adapter 에서 업데이트되는 position 항목만 호출하여 payload를 받아 뷰를 업데이트 할 수 있다.

## 예제
```
override fun onBindViewHolder(holder: ViewHolder, position: Int) {
    val user = data[position]
    holder.bind(user, position)
}

override fun onBindViewHolder(holder: ViewHolder, position: Int, payloads: MutableList<Any>) {
    if (payloads.isEmpty()) {
        super.onBindViewHolder(holder, position, payloads)
    } else {
        payloads.forEach { payload ->
            if (payload is String) {
                if (TextUtils.equals(payload, PAYLOAD_BOOKMARK)) {
                    val item = data[position]
                    val itemView = holder.itemView
                    setBookmark(itemView.layout_avatar, itemView.cb_follow, item, position)
                }
            }
        }
    }
}
```

## 참고
- [RecyclerView 에서 notifyItemChanged()의 payload 이해하기](https://zerogdev.blogspot.com/2018/07/recyclerview-notifyitemchanged-payload.html)
