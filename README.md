# 当前版本所生成的垃圾代码已经足够使用。暂时固定到当前commit，待我了解新的实现机制之后再行定夺是否需要更新。 by PAMPANG

# KLGenerateSpamCode 垃圾代码生成器
本工具用于应对苹果对重复应用的审核（Guideline 4.3 Design Spam），避免苹果机审检测概率。

## 主要功能
1. 扫描工程中的代码，生成同等数量的 Category 文件，文件中及是同等方法数量的垃圾代码，垃圾代码方法名随机。
1. 修改 xxx.xcassets 文件夹中的 png 资源文件名。
1. 删除代码中的所有注释和空行。

## 使用
1. 下载源码。
1. 用 Xcode 打开工程并配置参数。如图![配置参数](https://github.com/klaus01/KLGenerateSpamCode/raw/master/images/p1.png)￼
1. 运行，生成垃圾代码，处理 png 文件名。
1. 将生成的垃圾代码拖入工程中。

### 参数说明
- **工程源文件目录**（如：`/Users/kelei/Documents/work/git/projectName/source`）
- **-spamCodeOut** 后面跟垃圾代码输出目录（如：`-spamCodeOut /Users/kelei/Desktop/GSCCategory`）
- **-handleXcassets** 修改`xxx.xcassets`文件夹中的 png 资源文件名，同时也`Contents.json`文件中的关联名称，不会影响代码中使用图片。
- **-deleteComments** 删除工程目录下 .h .m 文件中的注释和空行。

## 已知问题
- 生成的垃圾代码文件可能是 .m 文件中实现的私有类，编译垃圾代码可能会报错，删除该垃圾代码 .h .m 文件及可。

## 另外修改图片 hash 值的方法
使用 [ImageMagick](http://www.imagemagick.org/) 对 png 图片做轻量压缩，及不损失图片质量，又可改变图片文件 hash 值。方法：
1. 安装 ImageMagick，`brew install imagemagick`
2. 压缩工程目录下所有 png 文件，`find . -iname "*.png" -exec echo {} \; -exec convert {} {} \;`

