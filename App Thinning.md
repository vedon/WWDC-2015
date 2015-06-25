##App Thinning 

###App Slicing
这一项功能只针对iOS 平台，Slicing就是创造并传输为不同目标设备而设计的变体应用包（variant,以下简称定制化下载包）的处理过程。**一个定制化下载包仅包含针对特定设备所需要的可执行架构以及资源**。你可以继续开发并且把完整版本的应用上传到iTunes Connect，然后App Store会根据玩家设备类型和分辨率创造并传输对应的应用。这里，你可以认为资源根据玩家设备分辨率和类型的不同而分割成了多种类型，GPU资源也根据设备能力进行了切分，当用户安装应用的时候，他们可以下载并安装适合自己设备的定制化应用包。**基本上来说项目里面用了Assets.xcassets就支持这个功能了**
![App Slicing Screenshot](./resource/Screen Shot 2015-06-18 at 2.57.20 PM.png)
新的Xcode7和App submit之后会对这些1x 2x 3x分辨率的Assets做一定的处理，让用户在下载的时候只下载自己所需要的Assets，这样至少可以在Assets上减掉很大一部分的体积。同时用户下载的时候只会下载到自己设备所需要的Architecture，32bit或者64bit。这样又能减小App的实际体积。
***
###On-Demand Resources(ODR)
On-Demand资源指的是你可以通过关键词和命令的方式进行分组归类的资源，比如图像和音频，App Store会把这些资源放在苹果服务器上并且为你管理下载。On-Demand资源可以加快下载速度并缩小应用包体，提高用户的首次登录体验。比如，一款游戏应用可以根据等级和任务的不同把资源分组，在玩家达到下一个等级或者完成一个任务之后才会用到后续的资源，同样，应用也可以只在用户进行IAP购买的时候提供对应的资源。

当一些on-demand资源不再需要而且磁盘空间较少的时候，操作系统会自动清除它们。如果你在App Store之外对自己的应用进行测试或者分发，那就需要你自己来管理这些On-Demand资源。需要注意的是，可执行的on-demand资源是不支持的，App Store也会对on-Demand资源进行分割（即上面说过的Slicing），进一步提高用户体验。想象一下，是否自己有种经历，就是当下载一个app ，等了很久之后，你会失去打开它的欲望。

对于用户们来说，on-demand资源是以透明的形式在后台运作的，当用户需要对应功能的时候，这些资源就会被提供。

[如何配置ODR](https://developer.apple.com/library/prerelease/ios/documentation/FileManagement/Conceptual/On_Demand_Resources_Guide/Chapters/IntroToODR.html#//apple_ref/doc/uid/TP40015083-CH2-SW1).

![On-Demand Resources Screenshot](./resource/Screen Shot 2015-06-18 at 2.57.26 PM.png)
***
###BitCode
Bitcode是一个已编译程序（Compiled Program）的中间代码（intermediate representation）。如果你上传到iTunes Connect里的应用包含bitcode的话，就可以被编译和链接到App Store。加入Bitcode可以让苹果在未来对你的应用二进制（app binary）进行再次优化，而不需要你向App Store提交新版本。

注意：对于iOS应用来说，Bitcode是默认但可选择的。如果你提供Bitcode，那么应用包里的所有应用和框架都需要加入Bitcode，而watchOS应用则必须加入Bitcode。