Android Signature Pad
====================

安卓签名板

Android签名板是一个用于绘制平滑签名的Android库,可以保存签名文件成jpg/svg文件到图库。它使用基于 [Smoother Signatures](http://corner.squareup.com/2012/07/smoother-signatures.html) post by [Square](https://squareup.com).

![Screenshot](https://github.com/gcacace/android-signaturepad/raw/master/header.png)



![Screenshot](https://github.com/maiduoduo/IRes/blob/master/picture/SignaturePad/Signature0610.jpg)

### 特点

* 平滑线的Bézier实现
* 基于速度的可变点大小
* 可定制的笔颜色和大小
* 位图和SVG支持
* 数据绑定



### 安装

最新版本的库可以在Maven Central上找到。



### For Gradle users

打开你的 `build.gradle` 并确保Maven Central repository声明为`repositories`部分：
```gradle
   repositories {
       mavenCentral()
   }
```
Then, include the library as dependency:
```gradle
compile 'com.github.gcacace:signature-pad:1.3.1'
```

### For Maven users

Add this dependency to your `pom.xml`:

```xml
<dependency>
  <groupId>com.github.gcacace</groupId>
  <artifactId>signature-pad</artifactId>
  <version>1.3.1</version>
  <type>aar</type>
</dependency>
```

### 用法


有关如何使用库的更详细的代码示例，请参考`/SignaturePad-Example`app,可以将demo下载下来本地运行查看。



1. 将依赖库控件“SignaturePad”视图添加到要显示的布局中。
```xml
 <com.github.gcacace.signaturepad.views.SignaturePad
     xmlns:android="http://schemas.android.com/apk/res/android"
     xmlns:app="http://schemas.android.com/apk/res-auto"
     android:id="@+id/signature_pad"
     android:layout_width="match_parent"
     android:layout_height="match_parent"
     app:penColor="@android:color/black"
     />
```

2. 配置属性。
* `penMinWidth` -笔划的最小宽度（默认值：3dp）。
* `penMaxWidth` -笔划的最大宽度（默认值：7dp）。
* `penColor` -笔划的颜色（默认值：颜色。黑色).
* `velocityFilterWeight` -用于根据以前的速度修改新速度的权重（默认值：0.9）。
* `clearOnDoubleClick` - 双击以清除焊盘（默认值：false）

3. 配置监听事件

可以在代码中设置“OnSignedListener”：

```java
 mSignaturePad = (SignaturePad) findViewById(R.id.signature_pad);
 mSignaturePad.setOnSignedListener(new SignaturePad.OnSignedListener() {
      @Override
      public void onStartSigning() {
          //Event triggered when the pad is touched
      }
     @Override
     public void onSigned() {
         //Event triggered when the pad is signed
     }
     @Override
     public void onClear() {
         //Event triggered when the pad is cleared
     }
 });
```



4. 监听获取用户签名数据

 * `getSignatureBitmap()` - 白底签名图。
 * `getTransparentSignatureBitmap()` - 具有透明背景的签名图。
 * `getSignatureSvg()` - svg格式签名。

## 数据绑定

“SignaturePad”视图具有所有监听事件的自定义数据绑定属性设置器：

```xml
 <com.github.gcacace.signaturepad.views.SignaturePad
     xmlns:android="http://schemas.android.com/apk/res/android"
     xmlns:bind="http://schemas.android.com/apk/res-auto"
     android:id="@+id/signature_pad"
     android:layout_width="match_parent"
     android:layout_height="match_parent"
     bind:onStartSigning="@{activity.onStartSigning}"
     bind:onSigned="@{activity.onSigned}"
     bind:onClear="@{activity.onClear}" />
```

## Cordova插件
多亏了[网友热议](https://github.com/netinhoteixeira网站/)，有一个Cordova插件正在使用该库。
请参考https://github.com/netinhoteixeira/cordova-plugin-signature-view。



## NativeScript插件

感谢[布拉德马丁](https://github.com/bradmartin)，有一个NativeScript插件。

请参考[https://github.com/bradmartin/nativescript-signaturepad](https://github.com/bradmartin/nativescript-signaturepad).

## 注意事项

当前不支持屏幕旋转。 Pull requests are welcome!

### 感谢
本库来自于[GianLuca](https://github.com/gcacace)的[android-signaturepad](https://github.com/gcacace/android-signaturepad)

## License

    Copyright 2014-2016 Gianluca Cacace

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
