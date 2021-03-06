# アプリのUIを作成する
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center_horizontal"
    android:orientation="vertical"
    android:padding="16dp"
    android:background="@color/backgroundColor"
    tools:context=".MainActivity">

    <!--  CALCULATE YOUR  -->
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="15dp"
        android:text="CALCULATE YOUR"
        android:textColor="@color/textColor"
        android:textSize="25sp"
        android:textStyle="bold"/>

    <!--  AGE  -->
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="15dp"
        android:padding="10dp"
        android:text="AGE"
        android:textColor="@color/ageTextColor"
        android:background="@color/ageTextBackgroundColor"
        android:textSize="25sp"
        android:textStyle="bold"/>

    <!--  IN MINUTES  -->
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="15dp"
        android:text="IN MINUTES"
        android:textColor="@color/textColor"
        android:textSize="25sp"
        android:textStyle="bold"/>

    <!--  Button(id:btnDatePicker)  クリックするとカレンダーが表示される -->
    <Button
        android:id="@+id/btnDatePicker"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="15dp"
        android:background="@color/white"
        android:text="Select Date"
        android:textColor="#929292"
        android:textSize="20sp"
        android:textStyle="bold"
        app:backgroundTint="@color/white"/>

    <!--  カレンダーでクリックした日/月/日を表示  -->
    <TextView
        android:id="@+id/tvSelectedDate"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="20dp"
        android:textColor="#844046"
        android:textSize="20sp" />

    <!--  Selected Date  -->
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textColor="@color/lightGreyTextColor"
        android:text="Selected Date"
        android:textSize="18sp"/>

    <!--  分を表示  -->
    <TextView
        android:id="@+id/tvSelectedDateInMinutes"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textColor="#844046"
        android:layout_marginTop="20dp"
        android:textSize="35sp"/>

    <!--  Age in minutes  -->
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textColor="@color/lightGreyTextColor"
        android:text="Age in minutes"
        android:textSize="18sp"/>

</LinearLayout>
```

## android:gravity
レイアウトの中の配置を決定する

|  値  |  説明 |
| ---- | ---- |
|  top  |  コンテナの一番上に配置される。サイズは変更されない。  |
|  bottom |  コンテナの一番下に配置される。サイズは変更されない。  |
|  left  |  コンテナの一番左に配置される。サイズは変更されない。  |
|  right  |  コンテナの一番右に配置される。サイズは変更されない。  |
|  center_vertical  |  コンテナの縦方向の真ん中に配置される。サイズは変更されない。  |
|  fill_vertical  |  高さをコンテナの高さにする。  |
|  center_horizontal  |  コンテナの横方向の真ん中に配置される。サイズは変更されない。  |
|  fill_horizontal  |  幅をコンテナの幅にする。  |
|  center  |  コンテナの真ん中に配置される。サイズは変更されない。  |
|  fill  |  高さと幅を、コンテナの高さと幅にする。  |
|  clip_vertical  |  topとbottomのオプションとして、上部もしくは下部をコンテナの境界にする。  |
|  clip_horizontal  |  leftとrightのオプションとして、左もしくは右をコンテナの境界にする。  |

## android:orientation
並べる方向を決める
|  horizontal  |  横方向  |
| ---- | ---- |
|  vertical |  縦方向  |
