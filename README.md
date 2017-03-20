# Video_Technic_master
序言

最近的项目中涉及到视频播放，在这里我把关于视频播放技术中的一些心得体会记录下来。

功能

https://github.com/huohu1007/Video_Technic_master/Screenshots/1.gif

完整演示



基本功能

1.在无wifi的情况下提示用户，包括正在播放的时候网络切换也会提示用户。


http://upload-images.jianshu.io/upload_images/2808681-312a0b2c8b8a16ab?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
2.小窗播放：当用户正在观看的视频没有播完，用户又滑动到其他页面则视频继续在小窗播放，播放完成以后小窗自动消失，并提示用户播放完毕。


http://upload-images.jianshu.io/upload_images/2808681-35a804ce91dcf974?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
播放完毕提示


http://upload-images.jianshu.io/upload_images/2808681-4f92282f03f5e190?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
3.列表播放：支持在列表中播放


http://upload-images.jianshu.io/upload_images/2808681-87e024c18660aff6?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
4.跨界面播放，在列表中播放时，点击列表进入详情页。或在小窗播放时点击小窗进入详情页。视频将继续播放，不会重头开始。

实现

关于视频在任意位置播放，我主要是通过一个VideoPlayManager来管理的。在VideoPlayManager中有一个用来播放视频的VideoPlayView，而在需要播放视频的时候通过Rxbus发送一个事件，事件包含了能够展示VideoPlayView的FragmeLayout和需要播放的视频资源。VideoPlayManager初始化的时候开启了一个线程用来检测当前视频需要播放的位置。
