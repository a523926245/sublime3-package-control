# sublime3-package-control
sublime3 package control install and solution
本人亲测可用，sublime3安装package control及install插件使用，时间2019/03/25
--------------------------------------------------------------------------
前言，第1次上git，也借机学习一下git的使用。
由于重新换了电脑，不得不重新安装一系列的软件，插件之类的。平常用sublime都习惯了，这次下了发现直接都是sublime3的版本了。
安装之后，想把自己之前用惯的一些插件装上，发现没办法安装package control 网上搜了各种方法，大概是2种

1：用代码安装，发现装不了，提示报错啥的(后面猜想应该是被墙了，找不到资源)

最简单的方式是通过Sublime Text 3的console命令界面进行安装
安装代码：import urllib.request,os,hashlib;
h = '6f4c264a24d933ce70df5dedcf1dcaee' + 'ebe013ee18cced0ef93d5f746d80ef60'; 
pf = 'Package Control.sublime-package'; 
ipp = sublime.installed_packages_path(); 
urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); 
by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); 
dh = hashlib.sha256(by).hexdigest(); 
print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by) 


2：手动安装，这个需要下载插件的安装包，结果还是很蛋疼，网站也被墙了https://packagecontrol.io/installation

所以很蛋疼啊，没插件的日子不好过，又不想换其他的编辑器！之后尝试把公司的拷回来用，发现也不行。感觉凉凉~~~~~

--------------------------------------------------------------------------
OK，不吹水了，直接上方案，某次巧合下发现某群友能翻墙，我突然想起请他帮忙下了1个package control安装包，然后回家自己动手，步骤如下

1:点击菜单Preferences > Browse Packages…

2:打开上一级文件夹到已安装的Packages所在文件夹 Installed Packages(总之找到这个文件夹)

3:把下载好的文件放到这个目录下(这个安装包我已经传在目录下PackageControl.sublime-package)

4：重启sublime,在菜单->preferences->Package Settings和package control选项，就说明安装package control成功了。

5：Ctrl + Shift + P 调出package control 输入install package确定
发现报错：There are no packages for installation
出现这种错误的原因是因为sublime中的包管理install package依赖一个channel_v3.json文件，
而这个json文件默认每次打开package control都会从一个网址下载，而当网址未响应的时候（实事证明经常出问题），就会出现报错。

6:下载资源中的channel_v3.json文件，放入本地任意目录(最好不会任意删除的)，
然后Preferences > package setting >package control > settings users

7:在代码中添加下面这一段，以我的放在E盘为例：
"channels":
	[
                "E:\\channel_v3.json"
		"http://static.bolin.site/channel_v3.json"   或者可以使用这个网上的资源地址
	]
8:重启sublime3，再Ctrl + Shift + P 调出 package control 输入install package
你会发现就可以了！


首次分享，亲喷！






