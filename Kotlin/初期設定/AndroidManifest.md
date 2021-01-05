# 色々と設定しておく

```
<activity
  android:name=".MainActivity"
  android:screenOrientation="portrait"
  android:theme="@style/NoActionBarTheme"
  android:windowSoftInputMode="adjustResize">
  <intent-filter>
      <action android:name="android.intent.action.MAIN" />

      <category android:name="android.intent.category.LAUNCHER" />
  </intent-filter>
</activity>
```

## android:screenOrientation="portrait"
画面を縦に固定する

## android:theme="@style/NoActionBarTheme"
アクションバーが表示されないようにする

これは別途theme.xmlにて下記のように設定が必要
```
<!--  アクションバーを表示しない  -->
<style name="NoActionBarTheme" parent="Theme.MaterialComponents.DayNight.NoActionBar">
  <!-- Primary brand color. -->
  <item name="colorPrimary">@color/purple_500</item>
  <item name="colorPrimaryVariant">@color/purple_700</item>
  <item name="colorOnPrimary">@color/white</item>
  <!-- Secondary brand color. -->
  <item name="colorSecondary">@color/teal_200</item>
  <item name="colorSecondaryVariant">@color/teal_700</item>
  <item name="colorOnSecondary">@color/black</item>
  <!-- Status bar color. -->
  <item name="android:statusBarColor" tools:targetApi="l">?attr/colorPrimaryVariant</item>
  <!-- Customize your theme here. -->
</style>
```

## android:windowSoftInputMode="adjustResize"
使用可能なスペースに合わせてレイアウトがサイズ変更されるようにする
