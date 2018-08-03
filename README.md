[![Download](https://api.bintray.com/packages/moreno/maven/fontbinder/images/download.svg)](https://bintray.com/moreno/maven/fontbinder/_latestVersion)
[![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-FontBinder-brightgreen.svg?style=flat)](http://android-arsenal.com/details/1/3829)
[![License](https://img.shields.io/badge/License-Apache%202.0-orange.svg)](https://opensource.org/licenses/Apache-2.0)

# FontBinder

Easy font usage in your Android XML layouts. This is a fork of **Lisa Wray**'s [**fontbinding**](https://github.com/lisawray/fontbinding).

* Based on [Data Binding](https://developer.android.com/topic/libraries/data-binding/index.html)
* Written in [Kotlin](http://kotlinlang.org)
* Automatic initialization
* Automatic font caching
* Homogeneous `android:font` usage
* Tiny size: **14 KB**
* Minimum Android SDK: **9**
* Available through jCenter


## Setup

#### Gradle

```gradle
android {
    ...
    dataBinding.enabled true
}

dependencies {
    compile 'com.github.nitrico.fontbinder:fontbinder:1.0.5'
    // kapt 'com.android.databinding:compiler:GRADLE_PLUGIN_VERSION' // this line only for Kotlin projects
}
```


## Usage

Simply use `android:font='@{"YourFontFileNameWithoutExtension"}'` in your TextViews:

```xml
<layout xmlns:android="http://schemas.android.com/apk/res/android">

    <RelativeLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent">

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Hello World!"
            android:font='@{"Alegreya-Bold"}'/>

    </RelativeLayout>

</layout>
```

* Make sure you use `<layout>` as root tag and write the quotation marks in the right way: `'@{"file"}'` or ```"@{`file`}"```
* Use `DataBindingUtil.setContentView(...)` or `DataBindingUtil.inflate(...)` to inflate your layouts
* Font files must be located in your `assets\fonts\` folder
* Android Studio may warn you in the `android:font` line with "unknown attribute", it's OK
* You might want to check [**LastAdapter**](https://github.com/nitrico/LastAdapter) to use it with RecyclerView


#### Cache

FontBinder **automatically caches used typefaces** to avoid recreating them in the future. To use the cached typefaces programmatically:

```java
// Java
mTextView.setTypeface(FontBinder.get("FontFileNameWithoutExtension"));
```
```kotlin
// Kotlin
mTextView.typeface = FontBinder["FontFileNameWithoutExtension"]
```


## License

```txt
Copyright 2016 Miguel Ángel Moreno
Copyright 2015 Lisa Wray

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
