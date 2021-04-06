# Room
SQLite全体を対象とする抽象化レイヤを提供し、SQLiteを最大限に活用しつつ、スムーズなデータベース アクセスを可能にする

# build.gradle(:app)ファイルに依存関係を追加
```
dependencies {
  def room_version = "2.2.6"

  implementation "androidx.room:room-runtime:$room_version"
  kapt "androidx.room:room-compiler:$room_version"

  // optional - Kotlin Extensions and Coroutines support for Room
  implementation "androidx.room:room-ktx:$room_version"

  // optional - Test helpers
  testImplementation "androidx.room:room-testing:$room_version"
}
```

## 3つのコンポーネントで構成
- データベース: データベース ホルダーを格納し、アプリの永続化リレーショナル データに対する基盤接続のメイン アクセス ポイントとして機能します。

  @Database アノテーション付きのクラスは、以下の条件を満たす必要があります。

    - RoomDatabase を拡張する抽象クラスであること。
    - データベースに関連付けられているエンティティのリストをアノテーション内に含めること。
    - 引数が 0 個で、@Dao アノテーション付きのクラスを返す抽象メソッドを含むこと。
    
   
  実行時に Room.databaseBuilder() または Room.inMemoryDatabaseBuilder() を呼び出すことで、Database のインスタンスを取得できる
  
- エンティティ: データベース内のテーブルを示します。
- DAO: データベースにアクセスする際に使用するメソッドを格納します。


User
```
@Entity
data class User(
  @PrimaryKey val uid: Int,
  @ColumnInfo(name = "first_name") val firstName: String?,
  @ColumnInfo(name = "last_name") val lastName: String?
)
```

UserDao
```
@Dao
interface UserDao {
	@Query("SELECT * FROM user")
	fun getAll(): List<User>

	@Query("SELECT * FROM user WHERE uid IN (:userIds)")
	fun loadAllByIds(userIds: IntArray): List<User>

	@Query("SELECT * FROM user WHERE first_name LIKE :first AND " +
				 "last_name LIKE :last LIMIT 1")
	fun findByName(first: String, last: String): User

	@Insert
	fun insertAll(vararg users: User)

	@Delete
	fun delete(user: User)
}
```

AppDatabase
```
@Database(entities = arrayOf(User::class), version = 1)
abstract class AppDatabase : RoomDatabase() {
	abstract fun userDao(): UserDao
}
```

下記のコードを使用することで作成したデータベースのインスタンスを取得できる
```
val db = Room.databaseBuilder(
		applicationContext,
		AppDatabase::class.java, "database-name"
).build()
```

[Roomについて](https://developer.android.com/training/data-storage/room?hl=ja)
