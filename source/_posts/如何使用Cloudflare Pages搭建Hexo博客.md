---
title: 如何使用Cloudfalre Pages搭建Hexo博客
date: 2022-1-25 09:40:55
tag: 
- Cloudflare Pages
- Hexo
---

# 一、前言

在七月二日我用[Hexo](https://hexo.io/ "Hexo")做了一个静态页博客，原本是打算用[Travis CI](https://travis-ci.org/ "Travis CI")进行自动化部署，然后经过朋友推荐尝试使用[GitHub Actions](https://github.com/features/actions "GitHub Actions")，两者都因为需要编写CI配置文件和部署麻烦，我都放弃了。我就打算使用[Cloudflare Pages](https://pages.cloudflare.com/ "Cloudflare Pages")来部署Hexo。接下来我将会介绍如何使用Cloudflare Pages来部署Hexo博客。

# 二、准备所需资源

## 1. 账户

首先准备以下账号。

[GitHub账号](https://github.com "GitHub") [Cloudflare账号](https://dash.cloudflare.com "Cloudflare")

GitHub账号与Cloudflare的账号网上都有注册方法我这里就不详细说明了。

## 2. 资源

<p style="font-size:1.25em">① 安装Node.js</p>

接下里就是资源准备。先从[Node.js](https://nodejs.org/zh-cn/download/ "Node.js")的官网下载Windows可用的Node.js安装到电脑

![Node.js下载页面](NodejsDownload.webp "Node.js下载页面")
<p style="text-align:center;color:grey;">Node.js下载页面</p>

点击“Windows 安装包”，下载完毕后打开。然后一直Next确认，直到出现Install字样，点击就会开始安装Node.js到电脑。

要注意安装完Node.js之后要重启电脑，环境变量才会生效。

<p style="font-size:1.25em">② 安装GitHub Desktop</p>

安装完毕后，我们要安装[GitHub Desktop](https://desktop.github.com/ "GitHub Desktop")到电脑，GitHub在[docs.github.com](https://docs.github.com/cn/desktop/installing-and-configuring-github-desktop/installing-and-authenticating-to-github-desktop/installing-github-desktop "GitHub Docs")详细写明了安装方法，这里便不再详细解释。

<p style="font-size:1.25em">③ 安装Hexo到文件夹</p>

然后我们新建一个空文件夹，然后打开PowerShell或者CMD，输入cd命令打开到刚才新建的文件夹，这里我们用“hexo”举例。

![新建文件夹并打开](New&OpenFolder.webp "新建文件夹并打开")
<p style="text-align:center;color:grey;">新建文件夹并打开</p>

然后我们输入`npm install hexo`来安装所需资源，文件会保存在文件夹的node_modules目录下。接下来显示的警告可以不用管。

![安装Hexo到文件夹](InstallHexo.webp "安装Hexo到文件夹")
<p style="text-align:center;color:grey;">安装Hexo到文件夹</p>

显示这些就算是安装完成了。

![安装Hexo到文件夹](InstallHexoOver.webp "安装Hexo到文件夹")
<p style="text-align:center;color:grey;">安装Hexo到文件夹</p>

<p style="font-size:1.25em">④ 生成Hexo资源目录</p>

然后我们输入`npx hexo init source`生成一个Hexo资源目录，名叫source。

![生成Hexo资源目录](NewSource.webp "生成Hexo资源目录")
<p style="text-align:center;color:grey;">生成Hexo资源目录</p>

显示这些就算是生成完成了。

![生成Hexo资源目录](NewSourceOver.webp "生成Hexo资源目录")
<p style="text-align:center;color:grey;">生成Hexo资源目录</p>

# 三、开始上传Hexo资源到GitHub仓库

## 1. 创建新的GitHub仓库

登录GitHub主页，然后在左边的Repository（仓库）一栏，点击New新建仓库。

![新建仓库](NewRepository.webp "新建仓库")
<p style="text-align:center;color:grey;">新建仓库</p>

然后在“Create a New Repository”一页，在“Repository Name”一栏输入你想要的仓库名称，这里我们以HexoBlog为例。要注意下面的仓库类型一定要选择**Public**而不是**Private**，然后点击下方的按钮“Create Repository”创建新的仓库。

![填写仓库信息](NewRepositoryInfo.webp "填写仓库信息")
<p style="text-align:center;color:grey;">填写仓库信息</p>

创建完之后就会自动跳转到我们的仓库页面，在这里可以控制仓库的各种属性。

![新的仓库](NewRepositoryOver.webp "新的仓库")
<p style="text-align:center;color:grey;">新的仓库</p>

## 2. 上传Hexo资源文件

<p style="font-size:1.25em">① 登录GitHub Desktop</p>

本人用的是GitHub Desktop作为GitHub的管理软件，所以这里用GitHub Desktop举例，也可以使用其他的软件，如[SourceTree](https://www.sourcetreeapp.com/)等，这里就不详细介绍了。首先我们打开GitHub Desktop，点击File并点击Options打开设置页面。

![打开GitHub Desktop设置](OpenOptions.webp "打开GitHub Desktop设置")
<p style="text-align:center;color:grey;">打开GitHub Desktop设置</p>

然后在弹出来的设置页面里点击Account选项。

![点击账户设置](ChooseAccount.webp "点击账户设置")
<p style="text-align:center;color:grey;">点击账户设置</p>

然后在右边点击“Sign In”。

![点击登录](SignIn.webp "点击登录")
<p style="text-align:center;color:grey;">点击登录</p>

然后在弹出来的界面中，点击“Sign in using your browser”（使用你的浏览器登录）

![使用浏览器登录](SignInBrowser.webp "使用浏览器登录")
<p style="text-align:center;color:grey;">使用浏览器登录</p>

然后在弹出来的浏览器网页中输入GitHub账户密码，并点击“Sign In”即可完成登录操作。

![输入账户密码](InputAccount.webp "输入账户密码")
<p style="text-align:center;color:grey;">输入账户密码</p>

登录完成后按照提示返回到GitHub Desktop即可。更多详细操作请看[docs.github.com](https://docs.github.com/cn/desktop/installing-and-configuring-github-desktop/installing-and-authenticating-to-github-desktop/authenticating-to-github)。

<p style="font-size:1.25em">② 上传Hexo资源文件到GitHub仓库</p>

打开我们的GitHub Desktop。我这里已经有仓库了，所以显示的界面应该和刚安装完的是不一样的。

![打开GitHub Desktop](OpenGitHubDesktop.webp "打开GitHub Desktop")
<p style="text-align:center;color:grey;">打开GitHub Desktop</p>

然后我们点击上方的File，然后点击Clone Repository。

![点击File并点击Clone Repository](ClickFile.webp "点击File并点击Clone Repository")
<p style="text-align:center;color:grey;">点击File并点击Clone Repository</p>

然后在弹出来的界面里点击我们刚才创建的仓库，然后点击Clone。

![Clone仓库到本地](CloneRepository.webp "Clone仓库到本地")
<p style="text-align:center;color:grey;">Clone仓库到本地</p>

等待仓库Clone完毕。

![Clone仓库到本地](CloningRepository.webp "Clone仓库到本地")
<p style="text-align:center;color:grey;">Clone仓库到本地</p>

然后我们在此界面点击“Show In Explorer”，就可以打开仓库的文件夹了。

![打开仓库文件夹](FinishCloning.webp "打开仓库文件夹")
<p style="text-align:center;color:grey;">打开仓库文件夹</p>

打开仓库文件夹之后，把生成好的Hexo资源目录移动到仓库文件夹里

![移动资源文件](MoveSource.webp "移动资源文件")
<p style="text-align:center;color:grey;">移动资源文件</p>

然后我们返回到GitHub Desktop，此时就能看见有新的更改。

![新的更改](NewChanges.webp "新的更改")
<p style="text-align:center;color:grey;">新的更改</p>

在左下角“Summary”一栏填写一个Commit名称，这里以“Update Flies”为例，点击‘Commit to Main“即可提交更改里。

![提交更改](CommitChanges.webp "提交更改")
<p style="text-align:center;color:grey;">提交更改</p>

然后在新界面里点击“Publish Branch”即可推送到仓库上。

![发布分支](PublishBranch.webp "发布分支")
<p style="text-align:center;color:grey;">发布分支</p>

返回GitHub仓库页面，即可看到文件都已经上传到仓库里了。

![上传文件到仓库](UploadFilesOver.webp "上传文件到仓库")
<p style="text-align:center;color:grey;">上传文件到仓库</p>

# 四、使用Cloudflare Pages进行自动化部署

## 1. 准备部署

登录Cloudflare Dashboard，在右边一排服务中点击“网页”。

![登录Cloudflare管理页](CloudflareDashboard.webp "登录Cloudflare管理页")
<p style="text-align:center;color:grey;">登录Cloudflare管理页</p>

然后在新的页面里点击“创建项目”。

![点击创建项目](NewProject.webp "点击创建项目")
<p style="text-align:center;color:grey;">点击创建项目</p>

此时Cloudflare便会要求给予GitHub权限来读取并拉取仓库资源。

![给予Cloudflare权限](CloudflareSignIn.webp "给予Cloudflare权限")
<p style="text-align:center;color:grey;">给予Cloudflare权限</p>

点击“Install & Authorize”确定，然后就会跳转到仓库选择页面，在这里选择你上传Hexo资源的仓库并点击开始设置。

![选择需要部署的仓库](SelectRepository.webp "选择需要部署的仓库")
<p style="text-align:center;color:grey;">选择需要部署的仓库</p>

## 2. 开始部署

在这里可以设置Pages显示的项目名称和分支。

![项目信息](PagesInfo.webp "项目信息")
<p style="text-align:center;color:grey;">项目信息</p>

接下来是最重要的设置，构建信息。在构建命令一栏填写`npm run clean && npm run build`，构建输出目录填写`public`

![构建信息](BuildInfo.webp "构建信息")
<p style="text-align:center;color:grey;">构建信息</p>

然后点击“保存并部署”，等待构建完成即可。

![等待构建完成](RunBuilding.webp "等待构建完成")
<p style="text-align:center;color:grey;">等待构建完成</p>

部署完成之后返回到项目主页，在“制作”一栏的“域”后面，就是Cloudflare Pages分配给你的链接，点击即可打开部署好的Hexo博客。此时所有部署工作已经完成。

![构建完成](BuildOver.webp "构建完成")
<p style="text-align:center;color:grey;">构建完成</p>

# 五、后记

到这里所有的部署工作已经全部完成了。你可以在后期给Hexo加上你自己喜欢的主题，我用的主题是[Yuzu](https://github.com/Cerallin/hexo-theme-yuzu)，你可以在[Hexo Themes](https://hexo.io/themes/)寻找你自己喜欢的主题。

也可以给Cloudflare Pages套上Cloudflare加速，我就不在这里详解设置方法了，各位用搜索引擎都搜得到配置方法的。

**然后，开始你的写作吧！**
