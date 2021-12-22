<a href="https://github.com/Jzvd/JiaoZiVideoPlayer" target="_blank"><p align="center"><img src="https://user-images.githubusercontent.com/2038071/ 42033014-0bf1c0b0-7b0e-11e8-811d-7639bcd294eb.png" alt="JiaoZiVideoPlayer" height="150px"></p></a>
-
<p align="center">
<a href="http://developer.android.com/index.html"><img src="https://img.shields.io/badge/platform-android-green.svg"></a>
<a href="http://search.maven.org/#artifactdetails%7Ccn.jzvd%7Cjiaozivideoplayer%7C7.4.2%7Caar"><img src="https://img.shields.io/badge/Maven% 20Central-7.4.2-green.svg"></a>
<a href="http://choosealicense.com/licenses/mit/"><img src="https://img.shields.io/badge/license-MIT-green.svg"></a>
<a href="https://android-arsenal.com/details/1/3269"><img src="https://img.shields.io/badge/Android%20Arsenal-jiaozivideoplayer-green.svg?style =true"></a>
</p>

Highly customizable Android video framework

## Pinned message:

The group owner WeChat entered the dumpling fan group, and the focus of communication shifted from the Q group to the WeChat group. WeChat: lipangit note JZVD, Q group: 490442439, 2 group: 761899104, verification information: jzvd, WeChat public account: jzvdjzt, QQ: 1066666651, [Telegram](https://t.me/jiaozitoken), [Weibo]( http://weibo.com/2342820395/profile?topnav=1&wvr=6&is_all=1), [public number article](https://github.com/Jzvd/JiaoZiVideoPlayer/wiki/%E5%85%AC%E4% BC%97%E5%8F%B7%E6%96%87%E7%AB%A0)



In order to increase the quality of the project, promote the progress of the project, invoke the power of the community, and facilitate community management, a digital token based on Ethereum ERC-20 [JiaoZiToken(JZT)(餃子Token)](https://github.com/JZVD) /JZT), there must be a lot to do.

#### [Find something to do to earn dumpling coins](https://github.com/Jzvd/JiaoZiVideoPlayer/wiki/%E6%89%BE%E7%82%B9%E4%BA%8B%E5%81 %9A%EF%BC%8C%E6%8C%A3%E7%82%B9%E9%A5%BA%E5%AD%90%E5%B8%81)

#### [Purchase consulting service to get dumpling coins](https://github.com/Jzvd/JiaoZiVideoPlayer/wiki/%E8%B4%AD%E4%B9%B0%E5%92%A8%E8%AF% A2%E6%9C%8D%E5%8A%A1%E9%80%81%E9%A5%BA%E5%AD%90%E5%B8%81)

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
