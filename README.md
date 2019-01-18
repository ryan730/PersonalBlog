## 前言
要说2018年最火的跨端技术，当属于 `Flutter` 莫属，应该没人质疑吧。一个新的技术的趋势，最明显的特征，就是它一定想把“前浪”拍死在沙滩上。这个前浪，就是"react Native","weex"。目前随便在搜索引擎上 搜索"Flutter reactNative",就全是这两个技术的对比，评测。

![image.png](https://user-gold-cdn.xitu.io/2019/1/18/16860949e91dce97?w=633&h=748&f=png&s=272485)

#### 一股股浓浓 :  不服来 “掰” 啊 ！！！的味道。

是的，错过了`react Native`, `weex` 这些 “炸” 翻前端的技术，不能在错过 `Flutter` 了，这年头，你不会一门，跨端技术，怎么好意思说自己是【前端】。

![timg.gif](https://user-gold-cdn.xitu.io/2019/1/18/16860949e9250de0?w=560&h=320&f=gif&s=919675)

Flutter是谷歌的移动UI框架，可以快速在iOS和Android上构建高质量的原生用户界面。 Flutter可以与现有的代码一起工作。在全世界... ... 
![image.png](https://user-gold-cdn.xitu.io/2019/1/18/16860949e9297312?w=226&h=240&f=png&s=57757)
### 好了, 这些，大家早就知道了，来点实在的！！！

话说隔壁师兄，“闲鱼” 是最早一批与谷歌展开合作，并在重要的商品详情页中使用flutter技术上线的BU。一路走来，积累了大量的开发经验。“闲鱼” flutter 相关文章的都很有深度，足见功力。
- [深入理解Flutter引擎线程模式](https://juejin.im/entry/5b20b5826fb9a01e5868d45f)
- [Android Flutter实践内存初探](https://segmentfault.com/a/1190000015452092)
- [深入理解flutter的编译原理与优化](https://blog.csdn.net/alitech2017/article/details/80937091)
- ... ...

### 都是一篇篇的深度好文，读完收益匪浅，但是对于刚接触 `Flutter` 的web前端同学来说还是
![image.png](https://user-gold-cdn.xitu.io/2019/1/18/16860949e9385440?w=219&h=150&f=png&s=35838)![image.png](https://user-gold-cdn.xitu.io/2019/1/18/16860949e9485b31?w=125&h=123&f=png&s=10610)![2E803E03-8FE3-4F5B-9943-51F9C54B3BF1.png](https://user-gold-cdn.xitu.io/2019/1/18/16860949e96b9c9b?w=195&h=154&f=png&s=38796)

好了，回到标题，笔者作为一名传统 web前端，想从前端最熟悉的视角 “躺” 着把 `Flutter` 了解一遍，不要敬仰，平视它！！！先从兴趣开始。

![](https://user-gold-cdn.xitu.io/2019/1/18/16860b336d89de0e?w=300&h=180&f=png&s=109396)
---

## 正文

Flutter 环境的搭建，其实有很多资源可以参考。这里就不累述了（知道有很多坑，在后续文章中,有机会把个人遇到的坑汇总一下 ）。

有兴趣可以参考 [flutter安装环境的搭建](https://flutter.io/docs/get-started/install) , 在这里建议各位，一定要自己亲自搭一下环境，跑一下官方demo, 小马过河，焉知深浅，自己定的位才是最准确的。

有了环境，[先配置编辑器](https://flutterchina.club/get-started/editor/#vscode)。

然后 [创建一个Flutter项目](https://flutter.io/docs/get-started/codelab)。

项目创建完成，可以先用 flutter run 跑一下。

```Dart
flutter run 
```
好了，跑起来了吧，你会看到一个计数的官方示例，点击加号图片可以做加运算。

这时候我们看项目的project 目录里 有一个入口文件叫 main.dart。然后打开 main.dart 就像下面这样:

![image.png](https://user-gold-cdn.xitu.io/2019/1/18/1686094a218bd411?w=724&h=216&f=png&s=51299) 

( 为什么你们看到代码比我的长，因为我折叠了!!! ) 这不是重点，重点是每个类继承的都是一个尾号为`Widget` 的字符。

聪明的你一定会觉得 `Widget` 和 `Flutter` 有着某种神秘的联系。


“Binggo！"，是的，`Flutter` 有两个重型武器，一个叫 `Dart` ,另一个就是 `Widget` 了。



#### `Dart` 一切皆来自 `Object`, `Flutter` 的组件皆来自 `Widget`。

> 关于强大的Dart,今天暂且不表,后面有时间可以独立篇幅来聊聊Dart。

先祭出一张 `Flutter` 的架构老图。
![image.png](https://user-gold-cdn.xitu.io/2019/1/18/1686094a4a805767?w=1080&h=563&f=png&s=205864)

在 `Flutter` 的世界里，包括views，view controllers，layouts等在内的概念都建立在Widget之上。

`Widget` 是 `Flutter` 组件的抽象描述。所以掌握Flutter的基础就是学会使用 `Widget`开始。

在Flutter界面渲染过程分为三个阶段：布局、绘制、合成，布局和绘制在Flutter框架中完成，合成则交由引擎负责：

![640.jpeg](https://user-gold-cdn.xitu.io/2019/1/18/1686094a4fdd731c?w=1080&h=567&f=jpeg&s=27314)

#### Flutter 通过组合、嵌套不同类型的控件，就可以构建出任意功能、任意复杂度的界面。
- 它包含的最主要的几个类有：

```javacripte

class WidgetsFlutterBinding extends BindingBase with GestureBinding, ServicesBinding, SchedulerBinding,PaintingBinding, RendererBinding, WidgetsBinding { ... }

abstract class Widget extends DiagnosticableTree { ... }
abstract class StatelessWidget extends Widget { ... }
abstract class StatefulWidget extends Widget { ... }
abstract class RenderObjectWidget extends Widget { ... }
abstract class Element extends DiagnosticableTree implements BuildContext { ... }
abstract class RenderObjectElement extends Element { ... }

class StatelessElement extends ComponentElement { ... }
class StatefulElement extends ComponentElement { ... }

```

> 上面这些类的主要作用如下:
- 基于Flutter控件系统开发的程序都需要使用WidgetsFlutterBinding，它是Flutter的控件框架和Flutter引擎的胶水层。
- Widget就是所有控件的基类，它本身所有的属性都是只读的。
- RenderObjectWidget所有的实现类则负责提供配置信息并创建具体的RenderObjectElement。
- Element是Flutter用来分离控件树和真正的渲染对象的中间层，控件用来描述对应的element属性，控件重建后可能会复用同一个element。
- RenderObjectElement持有真正负责布局、绘制和碰撞测试（hit test）的RenderObject对象。
- StatelessWidget和StatefulWidget并不会直接影响RenderObject创建，只负责创建对应的RenderObjectWidget
- StatelessElement和StatefulElement也是类似的功能。



#### 很复杂是吧，先不用管，简单表述Widget是这样的:

> Widget = 样式(css) + 标记语义(标签) + 组件化(官方) + 数据绑定(props) 

“什么？这不就是 react 吗？"
>  对， React 的概念和 `Flutter` 的 `Widget` 是有相通性的。 

“既然有react的概念,难道还有state,setState吗？“
> 又对, Flutter 还真有 类似 state 状态机制的概念，而且也确实有 setState 的方法。

“dome里有两个基类,StatelessWidget 和 StatefulWidget 是做什么用的？”
> StatelessWidget 和 StatefulWidget,这里两个类特别重要,几乎所有的组件都是基于他们创建的。

> StatelessWidget 是状态不可变的widget,称为 `无状态widget`。初始状态设置以后就不可再变化。如果需要变化需要重新创建。

> StatefulWidget 可以保存自己的状态,称为 `有状态widget`。`Flutter` 首先保存了初始化时创建的State,状态是通过改变State,来重新构建 `Widget` 树来进行UI变化。改变状态的方法，就是我们用的最多的神器"setState"，而单纯改变数据是不会引发UI改变的，这个概念和我们的 React 一样一样的。

#### 如果你是初次接触 `Flutter` 可以不用记忆这么多组件基类，只用记住以下式子就可以, 不夸张的说，熟悉这个式子就可以开发 Flutter 项目了:

![c4d850e3c04dd51db6cad9112f885e6b.png](https://user-gold-cdn.xitu.io/2019/1/18/1686094a5ff8fb7d?w=800&h=828&f=png&s=175531)

#### 拆解
围绕着widget的构成，我们来拆解分析一下，标记语义，样式，组件化。
---

### 标记语义

为什么不称为 “模版”,“标签”,“element" ，而叫"标记语义"，是因为flutter的 widget 结构并不只是 “模版”，“标签”，“element"。widget 描述结构更像是 React 的虚拟dom阶段，浓缩了相关上下文，以对象化的结构展示。

我们先来看看，React 创建出来的虚拟dom结构( 伪代码 ):

```javascripte
var newTree = el('div', {'id': 'container'}, [
    el('h1', {style: 'color: red'}, ['simple virtal dom']),
    el('p', ['Hello, virtual-dom']),
    el('ul', [el('li'), el('li')])
])
```
再来看看,flutter 用Dart 创建的 widget 代码结构：
```javascript
Widget build(BuildContext context) {
    return new Column(
      children: <Widget>[
        new Container(
          padding: new EdgeInsets.only(top:100.0),
          child: new Text('这是一个组件')
        ),
        new Container(
          decoration: new BoxDecoration(border: new Border.all(width:1.0,color: Colors.blue)),
          padding: new EdgeInsets.all(20.0),
          child: new Text('来自输入框:'+active)
        )
      ],
    );
  }
```
是不是这样看就熟悉很多了。

>  注:很多前端er 会不习惯这中书写方式，目前有开发者在社区推动，在编译前，使用jsx标签，编译后再解析成标记树,比如这个[DSX设计](https://spark-heroku-dsx.herokuapp.com/index.html)的提案。

虽然jsx->标记树 还只是提案，但其实可以帮助我们更容易理解,此提案想表达的样式像这样：
```javascript
class MyScaffold extends StatelessWidget {
  build(context) {
    return <Material>
      <Column>
          <MyAppBar
             title={<Text 
               text='Example title'
               style={Theme.of(context).primaryTextTheme.title},
             />}
          />
          <Expanded>
            <Center>
              <Text text='Hello, world!'/>
            </Center>
          </Expanded>
      </Column>
    </Material>;
  }
}

```
上面这段 jsx 要是用 Dart 来写是什么样的？如下:

```javascript
class MyScaffold extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Material(
      child: Column(
        children: <Widget>[
          MyAppBar(
            title: Text(
              'Example title',
               style: Theme.of(context).primaryTextTheme.title,
            ), // Text
          ), // MyAppBar
          Expanded(
            child: Center(
              child: Text('Hello, world!'),
            ), // Center
          ), // Expanded
        ], // <Widget>[]
      ), // Column
    ); // Material
  }
}

```

虽然 `Flutter` 与 react 这么类比多少有些牵强，但可以个人总结一些方法，方便理解：
- 开头大写的类名 相当于 jsx 的标签名
- child 相当于 jsx 的 子标签+布局
- children 相当于 jsx 的 群组子标签（和child还是有区别的)
- 其他属性相当于 jsx 的 props
- 大家有没有注意, 第二段dart 语法结尾都会带上 “ // ” 注释符号，这个是编辑器IDE在识别是 `Flutter` 项目后，自动追加上去的，像 jsx 语言的标签封闭，方便发现标注的起始节点。

---

### 样式

对于 `Flutter` 样式的理解,可以查看官方的这篇文档，也是同样用类比的方式，很直观的了解，HTML、css样式和 `flutter` 之间的联系.
可以参考这里：
https://flutter.io/docs/get-started/flutter-for/web-devs
https://flutterchina.club/web-analogs/

笔者摘选其中样例的重点部分，对比展示来说明( 由于篇幅问题, 父子关系css 结构，用tab方式来表示 ):

#### 文本样式：

<div style="display: flex;justify-content: space-between;">
   <div style="border: 1px solid gray;padding: 10px;border-radius: 5px; color: black;background: beige;width:48%;"><pre><code class="language-javascript">

.demo1 {
      background-color: #e0e0e0;
      width: 320px;
      height: 240px;
      font: 900 24px Georgia;
      letter-spacing: 4px; 
      text-transform: uppercase; 
    }

</code></pre>

</div>
   <div style="border: 1px solid gray;padding: 10px;border-radius: 5px; color: black;background: beige;width:48%;">

<pre><code class="language-javascript">

var demo1 = new Container( 
  child: new Text(
    "Lorem ipsum".toUpperCase(), // 对应 左边的文本转换大小写
    style: new TextStyle( // 对应 左边的 font
      fontSize: 24.0
      fontWeight: FontWeight.w900,
      fontFamily: "Georgia",
      letterSpacing: 4.0, 
    ),
  ),
  width: 320.0,  // 对应 左边的 width
  height: 240.0,  // 对应 左边的 height
  color: Colors.grey[300],  // 对应 左边的 background-color
);

</code></pre>

</div>
</div>

---

#### 样式居中：

<div style="display: flex;justify-content: space-between;">
   <div style="border: 1px solid gray;padding: 10px;border-radius: 5px; color: black;background: beige;width:48%;"><pre><code class="language-javascript">

.demo2 {
      display: flex;
      align-items: center;
      justify-content: center; 
    }

</code></pre>

</div>
   <div style="border: 1px solid gray;padding: 10px;border-radius: 5px; color: black;background: beige;width:48%;">

<pre><code class="language-javascript">

var demo2 = new Container(
  child:  new Center( // 对应左边的整个 flex 属性
    child:  new Text("Lorem ipsum"）
   )
  );
);

</code></pre>

</div>
</div>
---

#### 设置最大(小)宽度：

<div style="display: flex;justify-content: space-between;">
   <div style="border: 1px solid gray;padding: 10px;border-radius: 5px; color: black;background: beige;width:48%;"><pre><code class="language-javascript">
   
  .container{
   width:300px
   .demo3 {
      width: 100%;
      max-width: 240px; 
   }
  }

</code></pre>

</div>
   <div style="border: 1px solid gray;padding: 10px;border-radius: 5px; color: black;background: beige;width:48%;">

<pre><code class="language-javascript">

// 对于嵌套容器，如果父级的宽度小于子级宽度，则子级容器将自行调整大小以匹配父级。
var container = new Container(
   child: new Center(
        child: new Text("Lorem ipsum"),
        decoration: new BoxDecoration( ... ), // constraints属性,创建一个新的BoxConstraints来设置minWidth或maxWidth
        width: 240.0, // 对应左边的 max-width
    ),
   width:300.0
  ),
</code></pre>

</div>
</div>

---

#### 旋转组件：

<div style="display: flex;justify-content: space-between;">
   <div style="border: 1px solid gray;padding: 10px;border-radius: 5px; color: black;background: beige;width:48%;"><pre><code class="language-javascript">
   
 .redbox {
       transform: rotate(15deg); 
 }

</code></pre>

</div>
   <div style="border: 1px solid gray;padding: 10px;border-radius: 5px; color: black;background: beige;width:48%;">
<pre><code class="language-javascript">

var container = new Container( // gray box
    child:  new Transform( // 对应左边的 transform
      child:  new Container(  ... ),
      alignment: Alignment.center, // 对应左边的 transform
      transform: new Matrix4.identity() // 对应左边的 transform
        ..rotateZ(15 * 3.1415927 / 180),
    ), 
  )
);
</code></pre>

</div>
</div>

---

#### 缩放组件：

<div style="display: flex;justify-content: space-between;">
   <div style="border: 1px solid gray;padding: 10px;border-radius: 5px; color: black;background: beige;width:48%;"><pre><code class="language-javascript">
   
.redbox {
  transform: scale(1.5); 
}

</code></pre>

</div>
   <div style="border: 1px solid gray;padding: 10px;border-radius: 5px; color: black;background: beige;width:48%;"><pre><code class="language-javascript">

var container = new Container( // gray box
    child:  new Transform( // 对应左边的 transform
      child:  new Container(  ... ),
      alignment: Alignment.center, // 对应左边的 transform的中心
      transform: new Matrix4.identity() // 对应左边的 transform
        ..scale(1.5),
    ), 
  )
);

</code></pre>

</div>
</div>

---

#### 设置绝对位置和相对位置：

<div style="display: flex;justify-content: space-between;">
   <div style="border: 1px solid gray;padding: 10px;border-radius: 5px; color: black;background: beige;width:48%;"><pre><code class="language-javascript">
   
.greybox {
     position: relative; 
     .redbox {
       position: absolute;
       top: 24px;
       left: 24px; 
     }
}
</code></pre>

</div>
   <div style="border: 1px solid gray;padding: 10px;border-radius: 5px; color: black;background: beige;width:48%;"><pre><code class="language-javascript">

var container = new Container( // grey box
  child: new Stack( // 相对跟容器位置 relative
    children: [
      new Positioned( // 相对父容器位置 absolute
        child:  new Container( ... ),
        left: 24.0,
        top: 24.0,
      )],
  )
);

</code></pre>

</div>
</div>

---

#### 颜色渐变：

<div style="display: flex;justify-content: space-between;">
   <div style="border: 1px solid gray;padding: 10px;border-radius: 5px; color: black;background: beige;width:48%;"><pre><code class="language-javascript">

.redbox {
  background: linear-gradient(180deg, #ef5350, rgba(0, 0, 0, 0) 80%); 
}

</code></pre>

</div>
   <div style="border: 1px solid gray;padding: 10px;border-radius: 5px; color: black;background: beige;width:48%;"><pre><code class="language-javascript">

var container = new Container( // grey box
  child: new Center(
    child: new Container( // red box
      child: new Text( ... ),
      decoration: new BoxDecoration( 
        gradient: new LinearGradient( // 对应左边的 background: linear-gradient
          begin: const Alignment(0.0, -1.0),
          end: const Alignment(0.0, 0.6),
          colors: <Color>[
            const Color(0xffef5350),
            const Color(0x00ef5350)
          ],
        ),
      )
    ),
  )
);

</code></pre>

</div>
</div>

---

#### 圆角：

<div style="display: flex;justify-content: space-between;">
   <div style="border: 1px solid gray;padding: 10px;border-radius: 5px; color: black;background: beige;width:48%;"><pre><code class="language-javascript">

.redbox {
  border-radius: 8px; 
}

</code></pre>

</div>
   <div style="border: 1px solid gray;padding: 10px;border-radius: 5px; color: black;background: beige;width:48%;"><pre><code class="language-javascript">

var container = new Container( // grey box
  child: new Center(
    child: new Container( // red circle
      child: new Text( ... ),
      decoration: new BoxDecoration(
        borderRadius: new BorderRadius.all(
          const Radius.circular(8.0),
        ), 
      )
    ),
  )
);

</code></pre>

</div>
</div>

---

#### 阴影：

<div style="display: flex;justify-content: space-between;">
   <div style="border: 1px solid gray;padding: 10px;border-radius: 5px; color: black;background: beige;width:48%;"><pre><code class="language-javascript">

.redbox {
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.8),
              0 6px 20px rgba(0, 0, 0, 0.5);
}

</code></pre>

</div>
   <div style="border: 1px solid gray;padding: 10px;border-radius: 5px; color: black;background: beige;width:48%;"><pre><code class="language-javascript">

var container = new Container( // grey box
  child: new Center(
    child: new Container( // red box
      child: new Text( ... ),
      decoration: new BoxDecoration(
        boxShadow: <BoxShadow>[ // 对应左边的  box-shadow
          new BoxShadow (
            color: const Color(0xcc000000),
            offset: new Offset(0.0, 2.0),
            blurRadius: 4.0,
          ),
          new BoxShadow (
            color: const Color(0x80000000),
            offset: new Offset(0.0, 6.0),
            blurRadius: 20.0,
          ),
        ], 
      )
    ),
  )
);

</code></pre>

</div>
</div>

---

#### 画圆：

<div style="display: flex;justify-content: space-between;">
   <div style="border: 1px solid gray;padding: 10px;border-radius: 5px; color: black;background: beige;width:48%;"><pre><code class="language-javascript">

.redcircle {
  text-align: center;
  width: 160px;
  height: 160px;
  border-radius: 50%; 
}

</code></pre>

</div>
   <div style="border: 1px solid gray;padding: 10px;border-radius: 5px; color: black;background: beige;width:48%;"><pre><code class="language-javascript">

var container = new Container( // grey box
  child: new Center(
    child: new Container( // red circle
      child: new Text( ... ),
      decoration: new BoxDecoration(
        color: Colors.red[400],
        shape: BoxShape.circle, // 画圆和圆角不太一样，用的是BoxShape绘制图像能力
      ),
      width: 160.0,
      height: 160.0, 
    ),
  )
);

</code></pre>

</div>
</div>

---

#### 内联样式：

<div style="display: flex;justify-content: space-between;">
   <div style="border: 1px solid gray;padding: 10px;border-radius: 5px; color: black;background: beige;width:48%;"><pre><code class="language-javascript">

// css 的内联结构
.greybox {
    font: 900 24px Roboto; 
   .redbox {
       em {
          font: 300 48px Roboto;
          font-style: italic;
      }
    } 
}

</code></pre>

</div>
   <div style="border: 1px solid gray;padding: 10px;border-radius: 5px; color: black;background: beige;width:48%;"><pre><code class="language-javascript">

var container = new Container( // grey box
  child: new Center(
    child: new Container( // red box
      child:  new RichText(
        text: new TextSpan(
          style: bold24Roboto,
          children: <TextSpan>[
            new TextSpan(text: "Lorem "), // 继承内联样式
            new TextSpan(
              text: "ipsum",
              style: new TextStyle( // 具有自定义样式的单独样式
                fontWeight: FontWeight.w300,
                fontStyle: FontStyle.italic,
                fontSize: 48.0,
              ),
            ),
          ],
        ),
      ),
    ),
  )
);

</code></pre>

</div>
</div>

---

## 组件化

官方的[widgets目录](https://flutter.io/docs/development/ui/widgets)
![image.png](https://user-gold-cdn.xitu.io/2019/1/18/1686094a609364fd?w=952&h=734&f=png&s=111826)

点击每一个card后，里面还有子card, 以一个展开的纬度来看，是这样的:
![image.png](https://user-gold-cdn.xitu.io/2019/1/18/1686094a72cc1b2c?w=846&h=4685&f=png&s=478721)

这真是一个庞大的组件系统，这不是社区提供的，而是官方的。
flutter 团队事无巨细的实现了目前市面上基本上能见到的组件方式和类型。
个人认为这样做优缺点并存的。
先说缺点:
- 1.学习成本增加，曲线也还是比较陡峭的。

- 2.组件直接的继承关系路径比较零乱，比如 
  继承自 Widget 是这些大类道还清晰:
  PreferredSizeWidget ProxyWidget RenderObjectWidget StatefulWidget StatelessWidget。
  但是，StatelessWidget和StatefulWidget的子类就过于平行化了，名称上晦涩，没有抽象架构化，分层或者塔型级别。
> StatelessWidget：
![1EB00739-AA5A-4939-8EE9-7EBB5EC2AAA3.png](https://user-gold-cdn.xitu.io/2019/1/18/1686094a79761361?w=1125&h=320&f=jpeg&s=173323)

> StatefulWidget
![image.png](https://user-gold-cdn.xitu.io/2019/1/18/16860aec2818e2a9?w=1131&h=299&f=png&s=133618)

- 3.对自定义组件定义模糊，有这么庞大的组件库，到底以后是有个一个更系统的第三方组件库去替换它，还是说 `Flutter` 官方就不建议使用第三方组件,这个也未有定论。

再说优点：
- 1.可以阻止以后轮子泛滥，在团队僵持不下使用哪个轮子库时，最好的理由就是“官方”二字，因为使用官方，可以弱化和规避一些问题,比如: 版本迭代不同步，性能瓶颈，规范不统一等问题,也能快速支持官方的辅助工具。

- 2.正是由于官方的标准划一，为自动化编译，自动化搭建，测试调优，可视化带来便利，甚至为Ai前端模型化业务场景，提供支撑，都说前端的组件像搭`乐高`，`Flutter`就是颗粒标准统一的`乐高`。

- 3.天下之势，分久必合，合久必分。
  - 前端在经历了 `flash` 一统pc页面的富媒体时代，后被乔布斯和H5瓦解；
  - 之后又有`H5` 的繁盛和框架、语法、构建模式的乱战；
  - 再到有“别再更新，老子学不动"的呼声下，希望有个一统江湖的跨平台系统出现；
  - 让开发者更专注于，提高业务内容，创造 “新， 酷，炫” 的展现形势上下功夫。
  - 也许，真有一个前端江湖的王者的诞生。

    ![image.png](https://user-gold-cdn.xitu.io/2019/1/18/1686094a8feeab35?w=258&h=178&f=png&s=77094)

### 写在最后
实际的 `Flutter Widget` 要复杂的更多的多，在眼花缭乱的 `Widget` 组件中,笔者想用自己的一些理解，去粗取精，来逐步理解 `Flutter` 这个新家伙 ,文中有理解不到位的地方,欢迎大家指正。
笔者团队也正在开发一套《Flutter GO》的APP,帮助大家熟悉复杂的 `Flutter Widget`。
> 更多学习 Flutter的小伙伴，欢迎入QQ群 Flutter Go :679476515

> 《Flutter GO》项目地址 [alibaba/flutter-go](https://github.com/alibaba/flutter-go)

 ![image.png](https://user-gold-cdn.xitu.io/2019/1/18/16860ab806437997?w=345&h=717&f=gif&s=645292)
