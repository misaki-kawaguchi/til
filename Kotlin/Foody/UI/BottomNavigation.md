# Bottom Navigationを作成する

## com.google.android.material.bottomnavigation.BottomNavigationViewを追加する

```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
  xmlns:android="http://schemas.android.com/apk/res/android"
  xmlns:app="http://schemas.android.com/apk/res-auto"
  xmlns:tools="http://schemas.android.com/tools"
  android:layout_width="match_parent"
  android:layout_height="match_parent"
  android:background="@color/lightGray"
  tools:context=".MainActivity">

  <fragment
    android:id="@+id/navHostFragment"
    android:name="androidx.navigation.fragment.NavHostFragment"
    android:layout_width="0dp"
    android:layout_height="0dp"
    app:defaultNavHost="true"
    app:layout_constraintBottom_toTopOf="@+id/bottomNavigationView"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toTopOf="parent"
    app:navGraph="@navigation/my_nav" />

  <com.google.android.material.bottomnavigation.BottomNavigationView
    android:id="@+id/bottomNavigationView"
    android:layout_width="0dp"
    android:layout_height="wrap_content"
    app:layout_constraintBottom_toBottomOf="parent"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintHorizontal_bias="0.5"
    app:layout_constraintStart_toStartOf="parent"
    app:menu="@menu/bottom_nav_menu"/>

</androidx.constraintlayout.widget.ConstraintLayout>
```

## メニューを作成する
bottom_nav_menu.xml
```
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http://schemas.android.com/apk/res/android">

  <item android:id="@+id/recipesFragment"
    android:title="@string/recipes_fragment"
    android:icon="@drawable/ic_menu_book"/>

  <item android:id="@+id/favoriteRecipesFragment"
    android:title="@string/favorite_recipes_fragment"
    android:icon="@drawable/ic_star"/>

  <item android:id="@+id/foodJokeFragment"
    android:title="@string/food_joke_fragment"
    android:icon="@drawable/ic_food_joke"/>

</menu>
```

## MainActivityに処理を追加する
```
class MainActivity : AppCompatActivity() {

  private lateinit var navController: NavController

  override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)
    setContentView(R.layout.activity_main)

    navController = findNavController(R.id.navHostFragment)
    // Navigationボタンの挙動を管理する
    val appbarConfiguration = AppBarConfiguration(
      setOf(
        R.id.recipesFragment,
        R.id.favoriteRecipesFragment,
        R.id.foodJokeFragment
      )
    )

    // setupWithNavController() を呼び出す
    bottomNavigationView.setupWithNavController(navController)
    // デフォルトアクションバーにナビゲーションサポートを追加する
    setupActionBarWithNavController(navController, appbarConfiguration)
  }

  // 「上へ」ナビゲーションを処理する
  override fun onSupportNavigateUp(): Boolean {
    return navController.navigateUp() || super.onSupportNavigateUp()
  }
}

```
