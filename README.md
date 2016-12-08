# IOS童鞋注意啦🙄不需要android Studio 照样跨平台开发

首先当你看到这篇文章的时候，您应该各种环境已经配好了，如果环境还没配好的话，你可以看看[官方的配置](http://reactnative.cn/docs/0.39/getting-started.html#content)这里就不多提了，当你环境都配好了，接下来我们就要开始去准备东西了

   一.准备安卓第三方模拟器`Genymotion`,接下来就来体验安装步骤吧
   - 下载&安装VirtualBox虚拟机

![box.png](http://upload-images.jianshu.io/upload_images/1767433-9d635325ae1f4c52.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

   - 下载&安装 Genymotion：

![两个都得加进去.png](http://upload-images.jianshu.io/upload_images/1767433-1d168a30cde28f64.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![安装界面.png](http://upload-images.jianshu.io/upload_images/1767433-1257201ac2750f7d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


    以上两个下载地址在文章最后我会分享链接，当然你也可以自行谷歌下载
    大致的安装过程如下

- 注意一点`Genymotion`是需要官网注册下的，否则就不能添加模拟器了

- 如果觉得我的这个说的不太清楚的话，大家可以[点击这里](http://blog.csdn.net/sanyuancap/article/details/24806899)参考下流程，其实主要的还是在后面SDK配置上，否则模拟器跑不起来

二.踩了哪些坑点

- 首先第一个就是把`react-native`创建的代码传上git的坑(对安卓会出点问题)
  - 大家应该知道我们传到GitHub上后远程创库都得配一个`.gitignore`,这里由于是夸平台开发，所有你不能选OC,但是我还是选了，我是先随便选的，因为你肯定是要换掉的，[这是react-native.gitignore](https://github.com/facebook/react-native/blob/master/.gitignore),把里面的内容复制下来，给你刚刚随便选的那个.gitignore做编辑替换吧，记得提交代码仓库😯
  - 好了，上一步完成了后，这次我们要做的就是把远程仓库clone到本地来，`注意`,刚拉下来的代码，是没有`node_modules`文件夹的，我们需要把依赖库在本地通过
```obj
  npm install
```
当拉完后

执行`react-native run-android`
这会你如果刚刚本地的代码还在的话你可以打开安卓的看看,你会发现报错了
![报错1.png](http://upload-images.jianshu.io/upload_images/1767433-30070ef19e600533.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)从上面的报错信息应该不难判断是这个文件出问题了
![报错2.png](http://upload-images.jianshu.io/upload_images/1767433-d75032b71d7bbb8e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)接下来我们用sublime打开
![报错3.png](http://upload-images.jianshu.io/upload_images/1767433-e466f8a183f8fc6c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)你会发现这段代码出了事，因为系统它识别不了这个版本所有我们注释掉这段代码，但是你会发现，当你再跑的时候，还是报错
![报错4.png](http://upload-images.jianshu.io/upload_images/1767433-8d1ecddb8f020420.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)这次报错看第一行你会觉得是
`/Users/caixiang/Desktop/react-native-app/react-native/aZhiWo/android/app/build.gradle' line: 110`这个路径下文件出错了，但其实不然，它告知我们的一个消息说的是SDK找不到，所以版本才报错，这时细心的人应该会发现少了一个文件，没错是少了一个文件，这个文件就是那个被忽略的文件，你会发现用终端来执行 `react-native run-ios`没问题，程序跑起来了，但`react-native run-android`就会报错

![安卓缺少的文件.png](http://upload-images.jianshu.io/upload_images/1767433-9b41b25698f93bfa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)没错就是这个文件，这是一个安卓SDK路径配置的文件，因为每个人的SDK路径配置是不一样的，它是被`.gitignore`忽略了，所以这里我们得手动配置下，其实你可以把最开始自己本地创建的那个代码包里面去找找复制进入就没事了
![成功.png](http://upload-images.jianshu.io/upload_images/1767433-17b688747857f356.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)看到这样的界面就是成功了

最终运行的效果
![效果图.png](http://upload-images.jianshu.io/upload_images/1767433-625bc9c22f28c0e4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

`上面安卓的图片忘了放进安卓的包，只给IOS加入`

`第三方模拟器&虚拟机下载`链接: https://pan.baidu.com/s/1nvPjhFz 密码: 65nu

####以上就今天我这破电脑Android studio 连不上网，做了个小总结，即便没有Android studio 照样去安卓的模拟器上看效果，本文有一点可能没讲太清楚的地方应该就是模拟器的SDK的配置，这块身边有安卓的小伙伴的话，让他们教教就行。
