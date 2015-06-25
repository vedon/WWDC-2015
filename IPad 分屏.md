##Ipad 的分屏功能
支持分屏的设备有：

<img src="./resource/Screen Shot 2015-06-25 at 2.29.04 PM.png" alt="" width = "500">

在iOS 9 ```MPMoviePlayerController``` 和 ```MPMoviePlayerViewController``` 已经被 ```AVPlayerViewController``` 取代了。

<img src="./resource/Screen Shot 2015-06-25 at 2.25.23 PM.png" alt="" width = "500">

很遗憾，在自定义的播放器是没有办法做到分屏的功能。必须使用AVKit 里面的```AVPlayerViewController``` , AVFoundation 里面的 ```AVPictureInPictureController```. WebKit 里面的```WKWebView```。而且也仅支持iPad。
