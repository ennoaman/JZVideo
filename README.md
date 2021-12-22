
## Documentation

-[Document- API](https://github.com/Jzvd/JiaoZiVideoPlayer/wiki/%E6%96%87%E6%A1%A3-%E2%80%94-API), download and install [Demo jiaozivideoplayer- 7.4.2.apk](https://github.com/Jzvd/JiaoZiVideoPlayer/releases/download/v7.4.2/jiaozivideoplayer-7.4.2.apk), go through the Demo carefully
-[Document-Custom Jzvd](https://github.com/Jzvd/JiaoZiVideoPlayer/wiki/%E6%96%87%E6%A1%A3-%E2%80%94-%E8%87%AA% E5%AE%9A%E4%B9%89Jzvd), inherit JzvdStd to realize your own player
-[Document-Custom Play Kernel](https://github.com/Jzvd/JiaoZiVideoPlayer/wiki/%E6%96%87%E6%A1%A3-%E2%80%94-%E8%87%AA %E5%AE%9A%E4%B9%89%E6%92%AD%E6%94%BE%E5%86%85%E6%A0%B8), test which playback kernel is suitable for your project

## Effect

<img src="https://user-images.githubusercontent.com/2038071/78055336-fd0d3f00-73b5-11ea-83f2-b9c141d1d3c9.jpg" width="90%">

<img src="https://user-images.githubusercontent.com/2038071/76214561-f6245e00-6247-11ea-85bb-da35ede45463.gif" width="90%">

## QuickStart

1. Add a class library
```gradle
implementation'cn.jzvd:jiaozivideoplayer:7.4.2'
```

2. Add layout
```xml
<cn.jzvd.demo.CustomJzvd.MyJzvdStd
    android:id="@+id/jz_video"
    android:layout_width="match_parent"
    android:layout_height="200dp" />
```

3. Set the video address, thumbnail address, title
```java
MyJzvdStd jzvdStd = (MyJzvdStd) findViewById(R.id.jz_video);
jzvdStd.setUp("http://jzvd.nathen.cn/c6e3dc12a1154626b3476d9bf3bd7266/6b56c5f0dc31428083757a45764763b0-5287d2089db37e62345123a1be272f8b.mp4"
                            , "Dumplings close your eyes");
jzvdStd.posterImageView.setImage("http://p.qpic.cn/videoyun/0/2449_43b6f696980311e59ed467f22794e792_1/640");
```

4. In `Activity`
```java
@Override
public void onBackPressed() {
    if (Jzvd.backPress()) {
        return;
    }
    super.onBackPressed();
}
@Override
protected void onPause() {
    super.onPause();
    Jzvd.releaseAllVideos();
}
```

5. In `AndroidManifest.xml`
```
<activity
    android:name=".MainActivity"
    android:configChanges="orientation|screenSize|keyboardHidden"
    android:screenOrientation="portrait" /> <!-- or android:screenOrientation="landscape"-->
```

6. Add as needed in `proguard-rules.pro`
```
-keep public class cn.jzvd.JZMediaSystem {*;}
-keep public class cn.jzvd.demo.CustomMedia.CustomMedia {*;}
-keep public class cn.jzvd.demo.CustomMedia.JZMediaIjk {*;}
-keep public class cn.jzvd.demo.CustomMedia.JZMediaSystemAssertFolder {*;}

-keep class tv.danmaku.ijk.media.player.** {*;}
-dontwarn tv.danmaku.ijk.media.player.*
-keep interface tv.danmaku.ijk.media.player.** {*;}
```

Even if you customize the UI or modify the Library, you still have to go through the above steps to use the player.

## Notice:
1. After version 7.0, a layer of Layout should be placed outside JzvdStd
2. If the introduction of the configuration fails, check whether the Java 8 configuration is added according to the failed log, or upgrade the environment to the latest stable version

## JZVD DEMO description
<a href="https://gitee.com/FIUI/SYD_OTA/raw/master/JZVD.png" target="_blank"><p align="center"><img src="https://gitee. com/FIUI/SYD_OTA/raw/master/JZVD.png" alt="JiaoZiVideoPlayer"></p></a>

## License MIT

Copyright (c) 2015-2020 Li Pan

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge , publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING
BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
