# Kotlin-

# 来自安卓开发者的Kotlin简介

入门,kotlin

完整见链接 http://www.jianshu.com/p/6e288464a968


 因为公司的新技术调研 自己挑了Kotlin 然后就去看了下Kotlin 才发现真的是自己找坑跳啊
 
 【图片】
 
本文也只能简单介绍一下 后面细节先留坑 （反正也不一定会更新

# 1.什么是Kotlin

> Kotlin 是一个基于 JVM 的新的编程语言，由 JetBrains 开发。
Kotlin可以编译成Java字节码，也可以编译成JavaScript，方便在没有JVM的设备上运行。
JetBrains，作为目前广受欢迎的Java IDE IntelliJ 的提供商，在 Apache 许可下已经开源其Kotlin 编程语言。
--百度百科

简单的说就是一个可以运行在所有支持JAVA的设备上的语言啦

# 2. Kotlin For Android 
# why?
你是否已经厌倦了findViewByID？（什么？ButterKnife？ 写多了其实也不美观好吧

你是否已经看烦了model里面的getter和setter？

你是否觉得JAVA 6，7太过于冗长？

你是否快要被MVP里面的各种接口复写绕晕了？

...

# Welcome2Kotlin
[tupian]

以下调用不光包括Kotin 还有intellij用Kotlin写给安卓开发用的 ==Kotlin Extensions For Android==和==Anko==

*但是前者好像已经集成在AS 里面下载的Kotlin里面了*

**下面开始开车 坐稳了！！ 如果有点颠簸属于正常 我也是个新司机**

【图片】

1第一步开门

*此处都用AS作为IDE 因为Kotlin是JetBrains推的idea已经自带支持了*

**File-Settings-Plugins**

直接输入Kotlin进行搜索下载就可以啦

*小提示：需要将整个IDE都重启方可生效*

2.系安全带

个人觉得新建项目的话还是靠软件自动吧 小菜鸟比不过大牛对于Gradle配置不感冒 不过弄完还是建议和原生的JAVA去对比一下 万一以后出问题了还是能解决一下的

按平常一样创建一个Project但是记得选择**AddNoActivity**

*选错了也没太大问题可以讲JAVA代码自动转成Kotlin代码而且两者可完全可以共存*
*有点强大 小菜鸡瑟瑟发抖*

然后在AS里面右键选择新建KotlinActivity 之后待代码转换完成 点击上部提示AS就会自动帮你更改Gradle啦 

*同步要是很慢的话 同学你需要给AS配置科学上网了 要是还有有问题的话建议把版本改成你在AS下载的对应版本号*

打开代码 啊 如此清新 感受到了前所未有的清爽

和现代语言风格相近 没有 ； 没有各种基本类型 声明方法用fun等

【图片】

新建好了之后就可以试一试Kotlin了

【放开让我装逼】

3.开始试车

第一式 扔掉你findViewById和黄油刀

Kotlin Extensions For Android自带类似于Butter Knife的功能而且用起来会更简单

`import kotlinx.android.synthetic.main.activity_main.*`

看上去很多不好记 其实输完第一个后面接着几个都是首选项还是很简单的

之后你的所有View就可以通过ID来直接调用了 不明白？来举个栗子

【图片】

*注意命名方式 XML的下划线命名可以用但是会不美观 要 优雅 — —*

第二式 给你的Model瘦身

当我们随便打开一个Model文件 你会发现有用的不多 也就前几个变量声明 其他全是重复的getter&setter真的是受够了

然鹅 在kotlin里面是这样的

【图片】

然后就可以用JSON解释器去生成了！！真的太酷了。。

第三式 扩展一些基础类让你的代码更简单

有时候真的会很埋怨 为什么为什么这个class居然没有这个方法？？

去继承吧又太麻烦 忍一忍吧又实在是不行 而且有好几个控件可能都需要这个方法 这个时候就需要*扩展*了！

比如我想让Toolbar可以滑动的时候消失和出现 在任意一个类*一般会写一个Extension.kt*里面写上

```
fun Toolbar.slideExit(){
    if (translationY==0f) animate().translationY(-height.toFloat())
}

fun Toolbar.slideEnter(){
    if (translationY<0f)animate().translationY(0f)
}
```
然后就可以当作自带方法调用了 如果改成这样
```
fun View.slideExit(){
    if (translationY==0f) animate().translationY(-height.toFloat())
}

fun View.slideEnter(){
    if (translationY<0f)animate().translationY(0f)
}
```
就是所有的View都可以使用了 刺激~

脚的玛德·等一下 是不是觉得有一点点相识 对 没错 这种扩展方法可以用来替换掉我们的Utils 

【图片】

不过类似的Toast方法已经在 Kotlin Extensions For Android 里面有了 

*要是你没找到 也可能是在Anko里面 哈哈哈哈 
这两个库还是值得好好看看的 不光有很多可以简化你代码的方法 
还能了解一下Kotlin能干哪些 包括它的代码风格*

第四式 拥有实体方法的接口

简单粗暴直接上图

【图片】

Kotlin的接口可以自己把一些方法实体写上去 调用的时候只需要实例化参数就可以了 比如上图中的toolbar 

当然 也可以有没有尸体的方法 灵活处理

第五式 lamda表达式 

虽然JAVA 8已经有了 但是安卓还在JAVA 6·7啊。。

以后你的setOnClickListener()就可以是这样

【图片】

或者这样

【】

甚至是这样


【】

泪流满面

第六式 when 表达式

每次用到switch的时候 心中都是纠结万分 各种break case繁琐得要死 而且switch在安卓编程出现频率还不低

但是 我们现在有when了 不说了上代码

*写道这个后面有点懒了*

【图片】

第七式 代码里面写layout **需要Anko支持**

XML文件加载特别的费事费力 所以Kotlin&Kotlin是支持我们在代码里面布局的 

``` 
relativeLayout {
        val textView = textView("Sample text view") {
            textSize = 25f
        }.lparams {
            width = matchParent
            alignParentTop()
        }

        button("Sample button").lparams {
            width = matchParent
            below(textView)
        }
    }
```


说的好 我还是先用 XML 等以后迫不得已要优化再改吧 习惯了 而且这个貌似不能预览

[这里给一个dalao的文章链接][1]

第八式 空安全 

在Kotlin的世界里 没有null取代的是Unit 一个项目要是可以为空 声明是需要？标注 否则就一定不会为空

这样在编程的过程中 IDE就会自动帮你检查当前代码是不是会出现空报错了

*好了因为我比较喜欢7就写8个吧
买7赠一
（什么乱七八糟的借口 2333）
其实还有一些重要的特性  大家一起探索吧

# 结语

总之 从安卓开发者来看 Kotlin和JAVA 就类似于Swift和OC

它解决了JAVA上面的很多痛点 而且因为有Kotlin爹妈自己给android开发的组件 变得特别的适合写Android APP

但是它又不光只是一个JAVA的延伸还是有一些自己的思想在里面的 对于我这种弱鸡小白还是要花点时间学习的

**但是**
因为JAVA和Kotlin完全兼容 特别是 1.1.0之后也支持Dagger了

拿Kotlin写一些基础类 或者 工具类 还是不错的 反正背后有JetBrais支持

虽然Kotlin在TIOBE上排名很靠后但并不能说明它就不好或怎样

毕竟还没发展太久 相对Scala来说优势就在于简单和无缝的JAVA支持吧

再说了  不折腾一下和咸鱼有什么区别

附上几个Kotli学习链接

[Kotlin for android developers in chinese][2]

[Kotlin完整的中文教程][3]


  [1]: http://www.cnblogs.com/sunshine-anycall/p/5300305.html
  [2]: https://github.com/wangjiegulu/kotlin-for-android-developers-zh
  [3]: https://github.com/huanglizhuo/kotlin-in-chinese
