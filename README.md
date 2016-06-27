# gentoo-everywhere
install gentoo &amp; gentoo alternative to everywhere 

各位好，现在很多互联网公司，技术企业，实验室，都正在流行着在cluster上来开发自己项目，购买这种cluster服务，显然比自己组建维护要经济的多，而且就有更好的可伸缩性。比如我念书所在实验室和工作的时候所在的公司。

购买的cluster过内的有阿里云，腾讯云，亚马逊云，还有超算中心，我念书所在的学校就有自己的计算中心和cluster。

这些cluster上面大都运行着RHEL或是centos等古老的版本，比如腾讯机房用的就是tlinux1.2其实是centos6.5改过来的。

图1-1 腾讯机房的screenfetch截图

比如我们学校的cluster运行的是RHEL6.7 

图1-2 学校机房的screenfetch截图

等等，诸如此类，需要开发东西的时候就经常会遇到安装开发库的困难，大家知道linux的开发库是开发效率的根本保障，有了这些开发库，那么完成开发就很高效，但是这些库的部署和安装就遇到两个困难，1：没有root权限;2：有了root权限装上的库版本也过于古老。

要是联系运维的人给你装个库，那兼职就是百般折磨，最后就是说服他了，也得等排期，估计得排到明年的端午节。要是等运维的人把库给你装上。估计你早离职都换了三个工作了吧。

所以很多人都选择自己编译库，然后在configure的时候加上prefix参数，这样无需root权限，也可以安装上自己需要的库，索性linux的兼容性强，所以基本上不用看版本号，都能装上。然后通过配置环境变量LD_LIBRARY_PATH来加载自己编译的库。但是需要开发一个稍微上一些规模的项目的时候，那个LD_LIBRARY_PATH变量就是显示器小一些都一屏显示不下呀。

图1-3 腾讯机房工作开发环境LD_LIBRARY_PATH显示图

还有的时候，我们得到已经编译好的二进制包的时候，他需要更高的glibc版本，而centos/RHEL的glibc是2.12/2.14的，现在随便一个编译好的程序都得是glibc2.17起步吧。

比如安装tensorflow的时候，其他的依赖都好说，直接anaconda就能满足，然后直接pip install tensorflow.whl就好了。但是运行的时候就需要glibc2.17

图1-4 tensorflow缺少glibc2.17图

然后手动编译glibc2.17加载上之后，他又说缺少libstdc++ too old

图1-4 tensorflow 的libstdc++ too old图

这我就醉了，因为这个得重新编译高版本的gcc了。你们懂了吧，这是个多么艰巨的任务。


没时间写了，晚一些回来接着写。

## 参考文档
* https://archives.gentoo.org/gentoo-dev-announce/message/772326d735c8c7c469beffc0a9bb0b97
