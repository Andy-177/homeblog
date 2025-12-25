# 如何通过docsify搭建博客
## 准备工作
1.一个github账号

2.一个cloudflare账号

3.一个免费域名，要绑定好cloudflare
## 操作流程
1.在桌面上创建一个文件夹，什么名字都可以

2.新建index.html，使用文本编辑器打开

3.粘贴下面的代码到你的index.html里
```
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>你博客的名字</title>
  <!-- 主题样式（可选：vue.css、buble.css、dark.css等） -->
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/docsify@4/lib/themes/vue.css">
  <!-- 代码高亮样式 -->
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/prismjs@1/themes/prism-tomorrow.css">
</head>
<body>
  <!-- 内容会渲染到这个div -->
  <div id="app"></div>

  <script>
    // Docsify 配置
    window.$docsify = {
      name: "你博客的名字",  // 博客名称（显示在侧边栏顶部）
      repo: '',             // 可选：GitHub仓库地址（右上角会显示链接）
      loadSidebar: true,    // 启用侧边栏（读取_sidebar.md）
      maxLevel: 3,          // 目录最大层级（1-6）
      subMaxLevel: 2,       // 子标题显示层级
      homepage: 'README.md',// 首页文件（默认就是README.md，可省略）
      auto2top: true,       // 切换页面时自动滚动到顶部
      search: {             // 启用搜索功能（可选）
        placeholder: '搜索文章...',
        noData: '未找到结果',
        depth: 3
      }
    }
  </script>

  <!-- Docsify 核心库 -->
  <script src="https://cdn.jsdelivr.net/npm/docsify@4"></script>
  <!-- 代码高亮插件（支持多种语言） -->
  <script src="https://cdn.jsdelivr.net/npm/prismjs@1/components/prism-javascript.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/prismjs@1/components/prism-html.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/prismjs@1/components/prism-css.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/prismjs@1/components/prism-python.min.js"></script>
  <!-- 搜索插件 -->
  <script src="https://cdn.jsdelivr.net/npm/docsify@4/lib/plugins/search.min.js"></script>
  <!-- 图片缩放插件 -->
  <script src="https://cdn.jsdelivr.net/npm/docsify@4/lib/plugins/zoom-image.min.js"></script>
</body>
</html>
```
4.保存index.html，新建README.md，在README.md里面可以填写你的自我介绍，README相当于你的个人主页，别人第一眼看到的就是它，注意**README一定要是大写的**

5.新建_sidebar.md这个文件，这个控制你侧边栏显示的内容，你可以把你的文章挂在侧边栏，小白建议用下面的格式
```
- 首页
  - [欢迎页](/)  <!-- 对应 README.md -->

- 类别1
  - [文章名称](类别1/文章名称)
- 类别2
  - [文章名称](类别2/文章名称)
```
注意：用我的方法之后文章也要放入对应的文件夹里，类别1的文章就要放入类别1的文件夹

6.创建一个GitHub仓库，并取一个喜欢的名字，建议就取博客的名字，如果你是单纯的当博客分享内容，可以取名为blog，homepage

7.上传你的文件，上传完文件后创建一个名叫.nojekyll的文件，防止GitHub不识别开头带"_"的文件，导致侧边栏不识别

8.点击Settings，再点击Pages，找到Branch板块
找到这个板块后会看到下面有个`None🔽`的选择框，点击选择`main`，之后点`save`即可

9.找到Custom domain板块，下面有个输入框，填写你的域名，有些人可能注册的域名是`xxx.org`，但为了区分网站，加了个二级域名，就成了`abcd.xxx.org`，其中abcd就是你的二级域名，设定了二级域名就填写对应的二级域名

10.到cloudflare网站`https://dash.cloudflare.com/`，在首页点击你的域名，点击DNS选项卡，点记录

11.进入记录后，点添加记录，类型选CNAME，如果你不使用二级域名，那么`名称（必需）`下面的输入框填写`@`即可，如果是使用二级域名，直接填写二级域名部分即可（即`abcd.xxx.org`例子里的`abcd`）

12.`目标（必需）`下面填写`你的用户名.github.io`

13.点击保存，等待几分钟后你的博客网站就可以正常工作了
