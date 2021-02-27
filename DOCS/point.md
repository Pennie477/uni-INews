# 开发uniapp 用HBuilderX编辑器较好
因为`HbuilderX`对uni-app支持度高。因为uniapp与HBuilderX 都是DCloud公司产品。

# 软件安装版本号
开源软件版本类别
- `alpha版`:内部测试版。
- `beta版`：公开测试版。
- `rc版`：Release Candidate：候选版本。`预览版`。
- `stable版`：`稳定版` `最终发行版`

另外，对于商业软件，还有以下版本：
- `RTM版`：Release to Manufacture。`工厂版`。
- `OEM版`：`厂商定制版`。
- `EVAL版`：`评估版`。有30或者60天等使用期限的版本。
- `RTL版`：Retail.(`零售版`) `真正发售的版本`，有漂亮的包装、光盘、说明书等东西和高昂的价格。
[更多参考](https://blog.csdn.net/a3015440/article/details/6178568)

## HbuilderX安装下载
下载网址：https://www.dcloud.io/hbuilderx.html

下载`Alpha`的`app开发版`的 `HbuilderX`，
- `正式版`虽然稳定但是`Alpha`版包含更多内容。
- `标准版`虽小但是需要自己下载插件安装,`app开发版`内置好了所有开发uni-app所需的插件包。

安装：打开.exe文件即可使用


# git 版本回滚
 git reflog:查看版本号
 git reset --hard:版本号  回滚到对应版本号
 git reset --hard:check

# 本地建立了一个uni-INews项目，github上创建了一个同名仓库，如何合并
其实意思就是上传本地项目到远程仓库。

法1：github上 传本地文件。 之后再git clone url 下来进行开发
法2：通过git nash 未去了解

# 使用`vue-cli`的方式创建并运行项目
**创建项目：/终端**
- 首先检测系统中是否装有node`node -v`返回版本号即可。
- 全局安装vue-cli`npm i @vue-cli -g`
- 检测vue-cli是否安装成功`vue -V` 注意大写V，返回版本号即可。
- 创建项目`vue create -p dcloudio/uni-preset-vue test-uniapp`
	- 用vue 创建项目，借助dcloud的io包和uni-app的uni-preset-vue包 ，test-uniapp是项目名。
- 通过键盘上下键 选择模板，回车即可创建项目

# 开发uniapp项目的平台配置

uniapp项目会在微信小程序、app真机|模拟器、h5上开发。那么需要先配置这几个平台的环境。

**配置(微信)小程序平台环境**
- `微信开发者工具配置`:微信开发者工具/设置/安全设置 确保服务端口是开启状态，这样HX 才能正常拉起开发者工具。微信开发者工具[未下载?](https://developers.weixin.qq.com/miniprogram/dev/devtools/download.html)
- `HBuilderX配置`：HX中新建或打开一个项目后
  - mac：HX/HBuilderX/偏好设置运行设置/小程序运行设置
  - win：HX/工具/设置/运行设置/小程序运行设置
    - 微信开发者工具路径一般默认填好，如果HX没有正常拉起微信开发者工具或点击运行没有`微信小程序中运行`选择时，检查这里的配置。
      - mac中是微信开发者工具.app的路径
      - win中是微信开发者工具.exe的路径
      - 其他小程序的路径同理配置 
      - 注：微信开发者工具要下载稳定版本，不要下载其他版本，以保证正常拉起微信开发者工具
这样HX中写代码，微信开发者工具会实时显示效果  

**app真机平台配置**

**安卓真机连接HX**

手机设置/关于手机/版本号 点击5次 会打开开发者模式  / 打开USB调试 / 勾选传输文件/ 勾选始终允许使用这台计算机进行调试

检测连接情况：运行/是否出现对应手机的版本好的运行选项/选中运行项目。
- 会先自动安装调试基座（手机中点确认安装）
- 最后重启项目(控制台选项)

这样安卓真机上可以实时看到项目变化

**IOS真机连接HX**

IOS连接电脑/运行选对应项(没有则下载IOS手机助手之类的APP)


**IOS模拟器**
Mac: IOS模拟器

**H5平台配置**
- HX运行项目 可以运行到chrome或浏览器中说明已经可以运行到H5中了。
- 无则配置：
- 设置/运行设置/浏览器运行设置/填好浏览器路径

# uniapp项目 目录结构
- 1.`项目根目录/components`-自定义组件
- 2.`项目根目录/pages`-业务页面
- 3.`项目根目录/static`-静态文件-图片字体等
    放在static的文件会原样编译到页面，因此不能放JS等动态资源。
- 4.`项目根目录/unpackage/dist`-编译后的文件存放目录
- 5.`项目根目录/新建文件夹存放工具类` 如utils
- 6.`项目根目录/common` 公用文件，如公用样式。
- 7.`app.vue` 进入项目就会执行app.vue
	含一些应用声明周期函数  和  公用css
- 8.`main.js`应用入口-vue实例注册|全局变量的绑定|全局自定义组件的引入|三方库等
- 9.`manifest.json`项目配置-app图标|app启动图|appSDK配置|app模块权限|app原生插件|各个平台的配置等 源码视图：就是前面所有配置的代码表现
- 10.`pages.json`页面配置-每个页面都需在这里注册。更多参考：https://uniapp.dcloud.io/collocation/pages
    "globalStyle" 所有页面公用配置，若个别页面在注册时，用了同名的配置，会覆盖公用配置。
- 11.创建项目`readme.md`-告诉其他开发者 项目要怎么运行 或一些须知 以及项目基本情况。
- 12.`uni.scss`全局声明样式，提供了基本scss变量，可直接使用不需引入。也可在此编写其他变量。
l
# uniapp页面创建
勾选默认模板，勾选在pages.json中注册，勾选创建同名目录。
- 页面都是需要在pages.json中注册的，不自动注册则手动写
- 创建同名目录：给页面包裹一同名文件夹

# uniapp tabbar
tabBar底部选项卡
- 如果应用是一个多 tab 应用，可以通过 tabBar 配置项指定一级导航栏，并配置指定tab栏的表现，以及 tab 切换时显示的对应页。
- 其实就是应用底部，可以切换页面的导航栏。
- 优点：切换页面时，打开过的页面不会关闭,会缓存起来，重新打开时不会重新加载。(如何测试这功能?)
- 更多参考：https://uniapp.dcloud.io/collocation/pages?id=tabbar

./pages.json
- pages：注册页面与页面窗口表现，以及平台特有属性
- globalStyle：所有页面默认配置，pages节点中配置了相应属性会覆盖globalStyle的属性
- 除了这两个还有一个重要的版块：tabBar

**配置tabBar**
tabBar至少2个页面至多5个页面。因此新建两个页面。如pages/home/home.vue  pages/my/my.vue两个页面。

page.json中配置
```json
{
	"pages": [ 
    // ……
	],
	"globalStyle": {
    // ……
	},	
	// 1.tabBar接收一个对象
	"tabBar":{
		// 2.可以定义一些属性
		"color":"#666",			//灰色 tabBar的文字 默认颜色
		"selectedColor":"#ff5a5f",   //红色 选中时的默认颜色
		"borderStyle":"black",     //tabBar上面的border的 默认颜色
    // 3.这些属性这样子还没有与页面关联 

    // 4.通过list节点关联页面,赋值一个数组 元素：页面配置
    "list":[
      // 首页配置
      {
        "pagePath":"pages/index/index",  //页面路径
        "test":"首页",  //页面名词
        "iconPath":"static/home.png",    //页面图标，注意只能<40kb的本地图片, 尺寸建议：81*81px
        "selectedIconPath":"static/home-active.png"    //选中时的颜色
      },
      // 关于页面
      {}
      // 我的页面
      {}
    ]
	}	
}
```

