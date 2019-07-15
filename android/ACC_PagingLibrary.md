# Android Architecture Component - Paging library 

## Database examples
```kotlin 
@Dao
interface ConcertDao {
    // The Int type parameter tells Room to use a PositionalDataSource
    // object, with position-based loading under the hood.
    @Query("SELECT * FROM concerts ORDER BY date DESC")
    fun concertsByDate(): DataSource.Factory<Int, Concert>
}

class ConcertViewModel(concertDao: ConcertDao) : ViewModel() {
    val concertList: LiveData<PagedList<Concert>> =
            concertDao.concertsByDate().toLiveData(pageSize = 50)
}

class ConcertActivity : AppCompatActivity() {
    public override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        val viewModel = ViewModelProviders.of(this)
                .get<ConcertViewModel>()
        val recyclerView = findViewById(R.id.concert_list)
        val adapter = ConcertAdapter()
        viewModel.livePagedList.observe(this, PagedList(adapter::submitList))
        recyclerView.setAdapter(adapter)
    }
}

class ConcertAdapter() :
        PagedListAdapter<Concert, ConcertViewHolder>(DIFF_CALLBACK) {
    fun onBindViewHolder(holder: ConcertViewHolder, position: Int) {
        val concert: Concert? = getItem(position)

        // Note that "concert" is a placeholder if it's null.
        holder.bindTo(concert)
    }

    companion object {
        private val DIFF_CALLBACK = object :
                DiffUtil.ItemCallback<Concert>() {
            // Concert details may have changed if reloaded from the database,
            // but ID is fixed.
            override fun areItemsTheSame(oldConcert: Concert,
                    newConcert: Concert) = oldConcert.id == newConcert.id

            override fun areContentsTheSame(oldConcert: Concert,
                    newConcert: Concert) = oldConcert == newConcert
        }
    }
}
```

## 참고
- [Paging library overview ](https://developer.android.com/topic/libraries/architecture/paging/)
- [Paging Library, 그것이 쓰고싶다](https://medium.com/@jungil.han/paging-library-%EA%B7%B8%EA%B2%83%EC%9D%B4-%EC%93%B0%EA%B3%A0%EC%8B%B6%EB%8B%A4-bc2ab4d27b87)
- [Paging – DataSource 종류](https://www.charlezz.com/?p=599)