---
layout:     post
title:      "github pages+jekyll搭建博客(windows)"
subtitle:   "此文章教你如何使用github pages+jekyll搭建自己满意的博客"
date:       2017-05-16
author:     "zyw"
header-img: "img/2017-05-16/githubpages-jekyll.png"
navcolor:   "invert"
header-mask: 0.3
catalog:    true
tags:
    - github pages+jekyll
---

# 前言

先唠叨两句，说一下我的写博客经历，原来我就是在新浪写一写，后来发现对于程序员来说，并不是很好用，一些代码他会过滤，还会给你读出来，上次有一个input框，发布出去的时候居然出来一个搜索框，让我无言以对。代码高亮什么的效果都不好，还需要我把代码放到记事本里，在粘贴到博客里，很麻烦，也不美观，让后我就去博客园等一些地方，想在这些地方写写，后来想想觉得也不是很好，要不就自己做一套吧，我就用phpcms+bootstraps在本地搭建了一套，然后我觉得有点麻烦，写点什么也不方便，不直观，在加上还要去买服务器，然后就放弃了。后来发现了这个github pages感觉很不错，就像写txt是的，很方便，在加上一套jekyll模板，感觉还是很不错的，现在还很流行Hexo,下面有一块我会对比一下jekyll和Hexo的区别，优缺点。


# 一、github pages和jekyll介绍

首先先介绍一下github pages和jekyll

github pages其实就是github可以的为项目建立介绍站点，也可以用来建立个人博客的一个地方。个人觉得其实和新浪博客差不多。

jekyll是一款比较流行的静态博客框架其他的还有Jekyll，Hexo，Simple，Octopress，Pelican以及Lo·gecho等等。这些静态程序可以说都有各自的好处。在这里我就比较一下jekyll和Hexo

1.Jeky基于Ruby实现，安装Jeky需要搭建Ruby环境，在Windows搭建Ruby环境并不是被推荐的，而 Hexo基于NodeJs实现，在Windows上安装NodeJs开发环境简单。

2.Jekyll没有本地服务器，无法实现本地博文预览功能，需要上传到WEB容器中才能预览功能，而Hexo可以通过简单的命令实现本地的预览，并直接发布到WEB容器中实现同步。

3.比较直接的另一个原因是在网上查找了很多博客的主题，发现Jekyll官网提供的主题都不怎么好看(可能是个人原因)，而Hexo的主题看的比较顺眼。

4.两者都支持Markdown语法。

比较了一下感觉Hexo更好哈，我选择了jekyll的原因是因为当我选择了用github pages做博客的时候，官方推荐的就是jekyll,让后又看到了黄玄[Hux Blog](https://huangxuan.me)的博客，感觉他的模板很不错，所以就选择了使用jekyll。看完这篇文章，相信想用Hexo也方便理解很多。

# 二、jekyll安装和配置
其实你不在本地安装jekyll也可以的，在本地安装的好处就是你在本地写的代码可以随时查看，修改，监测，而不需要在传到github上，这样太麻烦了。

要安装jekyll首先需要安装ruby[下载地址](http://rubyinstaller.org/downloads/)下载好了之后就是一路的next,可以根据个人选择安装到那个盘，选择相应的位数进行下载。
![](/img/2017-05-16/ruby.png)
进行到这一步的时候把第二个选上，安装一下环境，当然全选也无所谓哦，安装好之后就可以不管他了，后面也用不到，但是没有他还真不行。
![](/img/2017-05-16/rubyinstall.png)
安装好ruby之后就是安装RubyDevKit[下载地址](http://rubyinstaller.org/downloads/)和ruby的地址是一个，只需要往下拉就可以看到这个画面,在这里要注意一点ruby2.0以上的版本从下面两个下载，还有一点你ruby安装的32位在这就要下载32位,64位就下载64位。最好安装最新的吧。位置最好和ruby在相同的盘里。
![](/img/2017-05-16/devkit.png)
都安装好之后就要进行配置了，首先打开安装的RubyDevKit的文件夹cmd进入（小黑框！！）输入命令
{% highlight ruby %}
   ruby dk.rb init
{% endhighlight %}
此时看一下你的RubyDevKit文件夹会生成一个config.yml配置文件，记录了系统安装ruby的位置。
然后是就要开始安装jykell了，首先要把安装源变为国内的。
删除旧的安装源：
{% highlight ruby %}
   gem sources --remove https://rubygems.org/
{% endhighlight %}
添加新的安装源：
{% highlight ruby %}
   gem sources -a http://gems.ruby-china.org/
{% endhighlight %}
不放心的话可以确认一下安装源：
{% highlight ruby %}
   gem source -l
{% endhighlight %}
开始安装jekyll
{% highlight ruby %}
   gem install jekyll
{% endhighlight %}
安装成功后就是要写我们的博客了，在这建议大家去网上找一找好看的模板直接fork下来，这样方便快捷，非常省时间，在这里我要感谢黄玄[Hux Blog](https://huangxuan.me)，我就是从他这里fork的，欢迎借鉴参考。

找到一个好的模板fork下来之后，把文件夹名字改为githubname.github.io(比如我的就叫zywkuo.github.io)
一个基本的 Jekyll 网站的目录结构一般是像这样的：
{% highlight ruby %}
   .
   ├── _config.yml
   ├── _drafts
   |   ├── begin-with-the-crazy-ideas.textile
   |   └── on-simplicity-in-technology.markdown
   ├── _includes
   |   ├── footer.html
   |   └── header.html
   ├── _layouts
   |   ├── default.html
   |   └── post.html
   ├── _posts
   |   ├── 2007-10-29-why-every-programmer-should-play-nethack.textile
   |   └── 2009-04-26-barcamp-boston-4-roundup.textile
   ├── _data
   |   └── members.yml
   ├── _site
   └── index.html
{% endhighlight %}
来看看这些都有什么用：
{% highlight ruby %}
_config.yml	    存储配置数据。很多全局的配置或者指令写在这里。
_drafts         存放为发表的文章。这些是没有日期的文件。
_includes       你可以加载这些包含部分到你的布局或者文章中以方便重用。
_layouts 	    布局、模板。
_posts 	        存放写文章，格式化为：YEAR-MONTH-DAY-title.md。
_site 	        最终生成的博客文件就在这里。
index.html	    博客的主页。
other 	        例如静态文件 CSS，Images 和其他。
{% endhighlight %}
进入这个文件夹再次使用cmd(小黑框)，运行命令
{% highlight ruby %}
jekyll serve
{% endhighlight %}
当我运行启动服务器的命令的时候办了这个错误
{% highlight ruby %}
  Dependency Error: Yikes! It looks like you don't have jekyll-paginate or one of its dependencies installed. In order to use Jekyll as currently configured, you'll need to install this gem. The full error message from Ruby is: 'cannot load such file -- jekyll-paginate' If you run into trouble, you can find helpful resources at https://jekyllrb.com/help/!
jekyll 3.4.3 | Error:  jekyll-paginate
{% endhighlight %}
只需要在输入这个，回车就可以了
{% highlight ruby %}
gem install jekyll-paginate
{% endhighlight %}
再次输入无错误提示就说明服务器已经运行成功了，如果还有其他错误请自行百度吧。
{% highlight ruby %}
jekyll serve
{% endhighlight %}
此时打开浏览器在地址栏输入下面的网址就可以看到你的博客了
{% highlight ruby %}
localhost:4000或127.0.0.1:4000
{% endhighlight %}
在写自己的博客的时候需要多次的去浏览器看博客在网页上的显示情况只需要输入下面的就可以对你的代码就行实时监测，实时更新了。
{% highlight ruby %}
jekyll serve --watch
{% endhighlight %}
当要写博客的时候只需要在_posts文件夹下新建一个.markdown的文件，次文件的命名要遵循这个原则。不能更改的。
{% highlight ruby %}
年-月-日-标题.markdown
{% endhighlight %}
# 三、github pages仓库建立
想要用github pages必须自己要有一个github账户这个不用多说了。进入到自己的github账户后，首先建立一个新的仓库，名称与本地的文件夹名称一样。
{% highlight ruby %}
githubname.guthub.io(我的就是zywkuo.github.io)
{% endhighlight %}
![](/img/2017-05-16/github1.png)
![](/img/2017-05-16/github2.png)
因为我已经建好了，所以显示已有。
# 四、将写好的博客放到github仓库上
在本地我们使用jykyll写好的博客，就可以放到，github上刚刚新建好的那个仓库这里，如何显示网页就交个giuhub吧，其实就是github上就有自带的jekyll,他会自动生成静态页的。

在做这一步的时候就需要会一些git指令了，并且还需要下载git(这个要是不会，度娘一下把。)

下载好了之后进入本地的githubname.github.io的文件夹，右击git bash(安装好git右击就会有的),初始化本地仓库：
{% highlight ruby %}
$ git init
注：git指令在输入的时候不需要加$，在执行每条指令自动加$,我是为了和上面的指令就行区分，所以git指令都加上了$
{% endhighlight %}
然后将本地的代码上传到仓库第一次需要这样执行
{% highlight ruby %}
$ git add .
$ git commit -a -m "注释信息"
$ git remote add origin https://github.com/username/repositoryname.git
$ git push origin master
{% endhighlight %}
以后再上传就可以这样执行了
{% highlight ruby %}
$ git add .
$ git commit -a -m "注释信息"
$ git push origin master
{% endhighlight %}
开始的时候我在网上发现之前有一些做法是需要创建一个叫做gh-pages的分支并且在这个分支进行操作，经过我的测试，可能这个适用于之前的版本，目前只需要将代码直接上传到主分支master就可以了。

此时你可以访问网址看看自己的博客了。
{% highlight ruby %}
githubname.github.io(不要忘了换成自己的github名字)
{% endhighlight %}
# 五、绑定自己的域名
在这里我就介绍如何绑定二级域名，一级域名绑定其实和二级的差不多，更加简单。
首先找到自己github上新建的那个githuname.github.io的仓库进入到设置页面
![](/img/2017-05-16/github3.png)
往下拉找到这个位置在input框里输入域名，blog.lihaikuo.com.一级域名就直接输入lihaikuo.com就可以了
![](/img/2017-05-16/github4.png)
你需要在根目录新建一个文件名为CNAME的文件，这个文件不需要添加任何后缀，在文件里写上bolg.lihaikuo.com(顶级域名就写lihaikuo.com)，让后上传到github上githubname.github.io的仓库上
然后去你购买的域名网站去进行域名解析，我的域名是在百度云上买的，在域名解析页面添加一条这样的解析指令
{% highlight ruby %}
添加一个CNAME，主机记录写blog，后面记录值写上你的zywkuo.github.io.
blog      CNAME    githubname.github.io.（最后面还有一个‘.’不要忘记）
{% endhighlight %}
![](/img/2017-05-16/github5.png)
一级域名主机记录写www就好了。如果不可以，在加上这两条解析就OK了。
{% highlight ruby %}
@          A             192.30.252.153
@          A             192.30.252.154
{% endhighlight %}
等上10分钟，访问一下你的网址看看成效吧----->[blog.lihaikuo.com](http://blog.lihaikuo.com/)

注：此篇博客发表时间2017-05-16，随着时间迁移，或许会越来越方便，最近观看的小伙帮肯定没问题，以后有可能会改版，就像我在找资料的时候也走进了很多坑。希望小伙伴们多多注意。






Finally, thanks for reading

































