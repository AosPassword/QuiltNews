#被窝资讯    
##一、创意来源及背景
手机作为作为一种方便快捷通讯工具，已经彻底融入了我们的生活当中，可以它说成为了我们日常获取信息的最主要的方式。现在当人们结束一天学习或工作的时候，睡在被窝里，都会习惯性地拿出手机来玩一会儿，于是我们便经常在朋友圈看到:啊！昨晚xx发布离婚声明啦，一时没忍住，刷了几个小时新闻，第二天的学习工作完全没精神了。经过我在朋友圈的调查发现，这是很多人都曾遇到过的情况。  

基于上述情况，我想开发一款能够控制打开app时间，控制新闻数量，并且提示你该睡觉的新闻客户端。其中的要包含一个“睡前”模块，可以不断下拉刷新，总会刷出你感兴趣的新闻，让你在获得自己满意的信息的同时，度过被窝里玩手机的那半个小时。  

我的开发理念是“睡前半小时，看尽天下事”。  
##二、系统功能设计图  


![](http://opil9ev82.bkt.clouddn.com/%E5%9B%BE%E7%89%87-0.png)
  
##三：功能详细设计  
####1．「热门」  
![](http://opil9ev82.bkt.clouddn.com/%E5%9B%BE%E7%89%87-1.png)
![](http://opil9ev82.bkt.clouddn.com/%E5%9B%BE%E7%89%87-2.png)    
“热门”界面汇集了当天的热门新闻(找个这样优质的API真是太不容易了，中途换了无数个)，几个小时会更新一次，每次显示10个频道，40条新闻，总共400条的优质新闻，达到了定量的效果。  

####2 .「视界」  
![](http://cfqxv.img48.wal8.com/img48/556291_20160902232720/1472831368.jpg)
![](http://cfqxv.img48.wal8.com/img48/556291_20160902232720/14728313698.jpg)  
“视界”界面主要内容是由七个热门的栏目构成，每个栏目下面五条视频，下拉可以刷新（苦逼的视频地址转换接口的要钱，虽然做了服务器缓存视频来源地址，但是那个地址有时效性，几个小时就要换一次，所以内容还是不敢展示多了）。所有的视频都是来自优酷，所以可以无限的下拉刷新，每天都会更新。  

视频的播放器用了一个开源库，自己也尝试去写了一下播放器，但是做出来有很多bug，用户体验太糟糕了，所以最后选择了前者。
####3．「睡前」  
![](http://opil9ev82.bkt.clouddn.com/%E5%9B%BE%E7%89%87-3.png)![](http://opil9ev82.bkt.clouddn.com/%E5%9B%BE%E7%89%87-4.png)   
“睡前”界面的设计理念是“睡前半小时，看尽天下事”，所以每次都只会显示五条新闻，采用下拉刷新的方式更新列表，每次下来都会刷新，总会刷出你想看的的新闻。  

还写了一个计时器来控制看新闻的时间，30分钟后就会停止刷新功能，并且显示一张比较温馨的图片，并提示用户该睡觉了。
####4．「我的」  
![](http://opil9ev82.bkt.clouddn.com/%E5%9B%BE%E7%89%87-5.png)![](http://opil9ev82.bkt.clouddn.com/%E5%9B%BE%E7%89%87-6.png)   

“我的”界面主要是进行一些常规的设置，比如“夜间模式”，”文字模式”等等，并且还可以查到自己的评论和收藏信息  
####5．「注册和登录」  
![](http://opil9ev82.bkt.clouddn.com/%E5%9B%BE%E7%89%87-7.png)![](http://opil9ev82.bkt.clouddn.com/%E5%9B%BE%E7%89%87-8.png)  
 引入了LeandCloud云后台，所有的用户信息都会保存在服务器，并且在登录界面和注册界面都会引导用户进行更方便快捷的QQ登录等方式。（QQ审核没通过）  
####4．「夜间模式和文字模式」  
![](http://opil9ev82.bkt.clouddn.com/%E5%9B%BE%E7%89%87-11.png)![](http://opil9ev82.bkt.clouddn.com/%E5%9B%BE%E7%89%87-12.png)  
  作为新闻APP，这两个功能还是必不可少的，方便了晚上的阅读和流量的节省。夜间模式要定义两套color，也着实花了我一些时间。  
##六、技术亮点
**系统架构**：整个代码框架采用了MVP设计模式，深度解耦,便于以后维护和升级。  

**网络请求**：使用的是RxJava+Retrofit框架结构，具有较高的访问效率。  

**Glide**:采用Google推荐的Glide图加载库，大大优化了整个app的图片加载效率，能够快捷的显示网络和本地缓存图片。  

**后台系统**：引入了LeanCloud后台管理系统，节省了后台开发时间，大大提高了开发效率。
  
##五：兼容性测试
**1.Testin云测试**  
软件写好后在Testin上面做了一个兼容性测试，发现通过率为98%，只有在两台总运存为512M，可运行内存低于70M的手机上运行一会儿会报ANR异常。  

![](http://opil9ev82.bkt.clouddn.com/%E4%BA%91%E6%B5%8B%E8%AF%95.png)    

**2.真机测试**  
在周围同学的手机上进行了真机测试，发现全部可以正常运行并使用相关功能。（手机包括：魅族、小米、联想、三星、htc，CUP从1GHZ到2.0GHZ,运存从1G到3G）  
##六、难点攻关
####整个过程碰到的难点还是挺多的，主要有以下方面：
**1.内容的选择与转换**  
作为咨询类APP，内容的选择肯定是最为重要的，然而网络上的接口质量普遍不高，我们花了大量的时间进行内容的筛选与转换，最后才选好合适的内容。内容选好就要考虑在移动端的展示问题，在移动端还要要考虑屏幕的大小和流量的消耗，那个“视界”模块的所有内容做下是最为复杂，因为来源是优酷视频，内容数量很多，但是要在手机上播放必须使用优酷的sdk，并且还有广告，这样用户体验极差，我们花了好多精力，最后在找到了将视频链接转换成视频url的方法，这样就没有了广告，用户体验也好了很多。  
**2.系统框架的搭建**  
 由于资讯类app频繁地涉及到了网络请求，我们必须保证其稳定性，因此立刻去学习了OkHttp、Rx	Java、Retrofit网络框架，学习成本真的很高，要从最基本的观察者模式开始学。这对我来说的确是一个挑战，不过最后还是做到了。  
**3.定时器的实现**  
由于“睡前”模块涉及到了限定观看时间的功能，我也是去恶补了很多关于handler，timer，message的相关知识，最后终于做出来了。

