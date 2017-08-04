# COGNITION


### 前言

    由于近几年前端的野蛮生长以及前端应用的多元化和复杂化，整个技术形态已经跟几年前纯做页面的时代完全迥异了。主要观念的变化总结来看在于一点，现在的前端开发面向的是web app而不是web page。今天的前端开发模式跟传统的GUI软件(如C++、.NET开发的windows客户端)已经很接近了，而且由于现在前端领域为了解决日益复杂的web业务需求及体量，越来越多的借鉴了传统客户端的开发经验，导致两者变得越来越趋同。再加上前端一些独特的特性(免安装、增量安装等)，工程上的复杂度有过之而无不及。前端如今已经脱离了茹毛饮血、刀耕火种的原始社会，开始步入了工业时代。


### 工程化
    MVC（Model-View-Controller）  BackboneJs、



    MVP（Model-View-Presenter）




    MVVM（Model-View-ViewModel）Angular 和 Ember



### 环境：
    Node.js 
        是一个基于 Chrome V8 引擎的 JavaScript 运行环境。 
        使用了一个事件驱动、非阻塞式 I/O 的模型，使其轻量又高效。 
        包管理器 npm，是全球最大的开源库生态系统。


### 构建工具：
    Grunt & Gulp
        自动化构建工具

            1. 全局安装 gulp：
                $ npm install --global gulp 
            2. 作为项目的开发依赖（devDependencies）安装：
                $ npm install --save-dev gulp

### 包管理工具：
    Npm
        主要运用于Node.js项目的内部依赖包管理，安装的模块位于项目根目录下的node_modules文件夹内
    Bower
        而Bower大部分情况下用于前端开发，对于CSS/JS/模板等内容进行依赖管理，依赖的下载目录结构可以自定义

        安装：
            $ npm install -g bower


### CSS预处理器
    Less & Sass
        基本思想是，用一种专门的编程语言，进行网页样式设计，然后再编译成正常的CSS文件

    Sass用法：

        1 变量
        SASS允许使用变量，所有变量以$开头。
            $blue : #1875e7;　
            　div {
            　　color : $blue;
            　}
        如果变量需要镶嵌在字符串之中，就必须需要写在#{}之中。
        　　$side : left;
        　　.rounded {
        　　　　border-#{$side}-radius: 5px;
        　　}

        2 计算功能
        SASS允许在代码中使用算式：
        　　body {
        　　　　margin: (14px/2);
        　　　　top: 50px + 100px;
        　　　　right: $var * 10%;
        　　}

        3 嵌套
        SASS允许选择器嵌套。比如，下面的CSS代码：
        　　div h1 {
        　　　　color : red;
        　　}
        可以写成：
        　　div {
        　　　　hi {
        　　　　　　color:red;
        　　　　}
        　　}
        属性也可以嵌套，比如border-color属性，可以写成：
        　　p {
        　　　　border: {
        　　　　　　color: red;
        　　　　}
        　　}
        注意，border后面必须加上冒号。
        在嵌套的代码块内，可以使用&引用父元素。比如a:hover伪类，可以写成：
        　　a {
        　　　　&:hover { color: #ffb3ff; }
        　　}

        4 注释
        SASS共有两种注释风格。
        标准的CSS注释 /* comment */ ，会保留到编译后的文件。
        单行注释 // comment，只保留在SASS源文件中，编译后被省略。
        在/*后面加一个感叹号，表示这是"重要注释"。即使是压缩模式编译，也会保留这行注释，通常可以用于声明版权信息。
        　　/*! 
        　　　　重要注释！
        　　*/

        5 代码的重用
        5.1 继承
        SASS允许一个选择器，继承另一个选择器。比如，现有class1：
        　　.class1 {
        　　　　border: 1px solid #ddd;
        　　}
        class2要继承class1，就要使用@extend命令：
        　　.class2 {
        　　　　@extend .class1;
        　　　　font-size:120%;
        　　}
        5.2 Mixin
        Mixin有点像C语言的宏（macro），是可以重用的代码块。
        使用@mixin命令，定义一个代码块。
        　　@mixin left {
        　　　　float: left;
        　　　　margin-left: 10px;
        　　}
        使用@include命令，调用这个mixin。
        　　div {
        　　　　@include left;
        　　}
        mixin的强大之处，在于可以指定参数和缺省值。
        　　@mixin left($value: 10px) {
        　　　　float: left;
        　　　　margin-right: $value;
        　　}
        使用的时候，根据需要加入参数：
        　　div {
        　　　　@include left(20px);
        　　}
        下面是一个mixin的实例，用来生成浏览器前缀。
        　　@mixin rounded($vert, $horz, $radius: 10px) {
        　　　　border-#{$vert}-#{$horz}-radius: $radius;
        　　　　-moz-border-radius-#{$vert}#{$horz}: $radius;
        　　　　-webkit-border-#{$vert}-#{$horz}-radius: $radius;
        　　}
        使用的时候，可以像下面这样调用：
        　　#navbar li { @include rounded(top, left); }
        　　#footer { @include rounded(top, left, 5px); }
        5.3 颜色函数
        SASS提供了一些内置的颜色函数，以便生成系列颜色。
        　　lighten(#cc3, 10%) // #d6d65c
        　　darken(#cc3, 10%) // #a3a329
        　　grayscale(#cc3) // #808080
        　　complement(#cc3) // #33c
        5.4 插入文件
        @import命令，用来插入外部文件。
        　　@import "path/filename.scss";
        如果插入的是.css文件，则等同于css的import命令。
        　　@import "foo.css";

        6 高级用法
        6.1 条件语句
        @if可以用来判断：
        　　p {
        　　　　@if 1 + 1 == 2 { border: 1px solid; }
        　　　　@if 5 < 3 { border: 2px dotted; }
        　　}
        配套的还有@else命令：
        　　@if lightness($color) > 30% {
        　　　　background-color: #000;
        　　} @else {
        　　　　background-color: #fff;
        　　}
        6.2 循环语句
        SASS支持for循环：
        　　@for $i from 1 to 10 {
        　　　　.border-#{$i} {
        　　　　　　border: #{$i}px solid blue;
        　　　　}
        　　}
        也支持while循环：
        　　$i: 6;
        　　@while $i > 0 {
        　　　　.item-#{$i} { width: 2em * $i; }
        　　　　$i: $i - 2;
        　　}
        each命令，作用与for类似：
        　　@each $member in a, b, c, d {
        　　　　.#{$member} {
        　　　　　　background-image: url("/image/#{$member}.jpg");
        　　　　}
        　　}
        6.3 自定义函数
        SASS允许用户编写自己的函数。
        　　@function double($n) {
        　　　　@return $n * 2;
        　　}
        　　#sidebar {
        　　　　width: double(5px);
        　　}


## 前端热门技术
### Angular &Vue & React

#### Angular：
    优点
    AngularJs是一套完整的框架，angular有自带的数据绑定、render渲染、angularUI库,过滤器,$filter,$directive(模板),$service(服务), $q(defer),$route, $http，$cookie, $inject(依赖注入),factory,provider……，等等一系列工具，基本上只要你在做web开发用过的东西，它都有一个。
    AngularJs的架构清晰，分工明确，扩展性良好，model，view，controller谁在什么时候做什么事情说的很清楚，angular能够让程序员真正专注于业务逻辑，对js能力要求也不高（基本上只需要写业务逻辑，实在用不上那些高级的js技巧和知识呀），而且因为对html侵入不大，非常易于和designer协作。整个框架充满了DI的思路，耦合性非常低，对象都是被inject的，也就是说每个对象都可以轻易被替换而不影响其他对象。
    Angular生产效率高，单向数据流什么的想法非常好，但是写起来太麻烦！我只想变更个很简单的数据还要经过action、dispatcher、store、view四步，angular里一行代码就搞定的事情在react里却如此麻烦
    Angular的背后是Google，所以社区基础是不用担心的，整个生态也已经是非常的完整了，从最基本的Tutorial到StackOverflow的问题数到框架本身的剖析都非常多，Angular上手比较容易。

    不足
    性能 
    同样是TODO MVC的Sample，Angular完全载入用了1.1s（WebPagetest - Visual Comparison）。React只用了0.3s,不得不说，确实挺慢的。。
    Angular 2.0推翻重做使得目前不宜采用此框架
    Angular 1.x版本其实是个比较旧的东西了，现在看来有些理念过时了，比如依赖注入、自己独特的模块化，这些东西其实在ES6下已经很好地被解决了。
    Angular的2.0几乎是一个推翻重做的框架，估计不会有1.X的upgrade方案。所以如果现在新开始的项目采用Angular的话，会是一个很尴尬的时机。同样，如此大的改动似乎也反面印证了1.X并不是那么好。

#### Vue：
    优点
    入门简单，可以让很多没做过后端开发的前端朋友从jquery开发思想中很快适应过来，即使不学习官网上【进阶的知识】也可以很好开发，在短平快的项目中发挥着巨大的作用。
    官方文档比较详情，而且还是中文的，我也买过一些书籍但是都不如官网文档清晰。
    框架轻量，渐进式插件众多，进阶式的开发理念，方便不同阶段的开发朋友。
    发展速度比较快，功能越来越强大。

    不足
    Vue中的指令太多了，这是一件相当痛苦的事情，记住并且灵活使用需要相当长的时间。 这里涉及了一个开发中一个理念：过多的配置，这些东西完全是框架设计者的个人思想。就比如很多开发人员都有类似的经历——通过大量的Json配置来提高开发效率，最后造成配置越来庞大，很难继续下去。
    Vue没有摆脱Jquery的束缚，使用Vue的朋友几乎无一例外的使用Jquery来做特效，Vue只是发挥了模版绑定，模块开发，页面功能上的组件开发而已


#### React：
    优点
    React伟大之处就在于，提出了Virtual Dom这种新颖的思路，并且这种思路衍生出了React Native，有可能会统一Web/Native开发。在性能方面，由于运用了Virtual Dom技术，Reactjs只在调用setState的时候会更新dom，而且还是先更新Virtual Dom，然后和实际Dom比较，最后再更新实际Dom。这个过程比起Angularjs的bind方式来说，一是更新dom的次数少，二是更新dom的内容少，速度肯定快。
    ReactJS更关注UI的组件化，和数据的单向更新，提出了FLUX架构的新概念，现在React可以直接用Js ES6语法了，然后通过webpack编译成浏览器兼容的ES5，开发效率上有些优势.
    React Native生成的App不是运行在WebView上，而是系统原生的UI，React通过jsx生成系统原生的UI，iOS和Android的React UI组件还是比较相似的，大量代码可以复用
    维护UI的状态,Angular 里面使用的是 $scope，在 React 里面使用的是 this.setState。 而 React 的好处在于，它更简单直观。所有的状态改变都只有唯一一个入口 this.setState()，Angular 就比较复杂，不知道背后使用了哪些黑魔法。

    不足
    React是目标是UI组件，通常可以和其它框架组合使用，目前并不适合单独做一个完整的框架。React 即使配上 Flux 的组合，也不能称之一个完整的框架，比如你想用Promise化的AJAX？对不起没有，自己找现成的库去。而且第三方组件远远不如Angular多。目前在大的稳定的项目上采用React的，我也就只知道有Yahoo的Email。React本身只是一个V而已，所以如果是大型项目想要一套完整的框架的话，也许还需要引入Flux和route相关的东西。而Angular在这方面提供的东西比React多多了.(其实，React给出了的是基本设计的思想：虚拟dom,jsx语法，单向数据流，组件开发……每一点都可引申出一系列的技术immutable,flux,redux,relay graphql,react native，还有前端架构的设计思想，让前端开发人员从页面重构师走向真正的程序员之路，掌握底层的东西。)



### 选择：ReactJs
## 发展的趋势
## React Native

    React Native的发布（2015年初）使得js统一三端(前端、后端、移动端)开发成为可能(现在这个时间点看可能还是过于理想，但是整体方向还是对的)，这一针强心剂吸引了大量开发者的眼球

### React

    核心特征
    virtual dom react中的组件跟页面真实dom之间会有一层virtual dom(虚拟dom)，virtual dom是内存中的javascript对象，它具有与真实dom一致的树状结构。开发者每次试图更新view，react都会重新构建virtual dom树，然后将其与上一次virtual dom树作对比，依靠react强劲的核心算法dom diff找出真正发生变更的节点，最后映射到真实dom上，这也是react号称性能高效的秘密所在。依赖于virtual dom，对React而言，每一次界面的更新都是整体更新，而不是层叠式更新(即一个复杂的，各个UI之间可能存在互相依赖的时候，每一次独立的更新可能会引发其他UI的变化，假如我们的目的是更新C的数据，逻辑流很可能是这样的 A -->B-->C-->A-->B–>C，这种情况下中间状态的DOM操作就是极大的浪费)。
    单向数据流 flux架构下的数据流呈现出一种单向、闭环的流动路线，使得一切行为变的可预测，也能更好的定位错误发生点。react官方的卖点之一就是 友好的错误提示
    每个组件都是状态机 react认为组件的数据模型是不可变的，组件的属性不应该被修改。组件关注的只应该是状态，不同的状态呈现不同的表现形式。每个状态下的组件都是一个virtual dom对象，这样react就能直接通过等号对比对象地址判断组件是否被修改从而是否需要更新dom，这也是其能提高性能的原因之一(空间换时间)。
    组件 一切都是组件 react倡导开发者将view切分成一个个组件从而达到松耦合及重用的目的。开发者构建页面只需要排列组合就行了。

#### 介绍
    相关技术：ECMAScript 6、Redux、Webpack

##### 小例 ：

```javascript

// es6

// react
import React, { Component, PropTypes } from "react";
import ReactDOM from "react-dom"; 

// component
class Container extends Component {
    // 
    constructor(props) {
        super(props);
        
        this.state = {
            title: 'Test'
            remark: 'clickMe'
        };
        
        this.handleChange = this.handleChange.bind(this);
    }
    
    componentWillMount() {
        console.log('Dom will insert...');
    }
    
    componentDidMount() {
        console.log('Dom had be insert...');
    }
    
    componentWillUpdate(nextProps, nextState) {
        console.log('Dom will be update...', nextProps, nextState);
    }
    
    componentDidUpdate(preProps, preState) {
        console.log('Dom had be update...', preProps, preState);
    }
    
    shouldComponentUpdate(nextProps, nextState) {
         return (nextProps.content !== this.props.content) ||
                (nextState.title !== this.state.title);
         
         console.log('shouldComponentUpdate...');         
    }
    
    componentWillReceiveProps(nextProps) {
        console.log('nextProps...');
    }
    
    componentWillUnmount() {
        this.setState({
            title: 'Test'
        });
        
        console.log('Dom will be remove...');
    }
        
    handleChange() {
        this.setState({
            title: 'React'
        });
    }
    
    render() {
        
         let { content } = this.props;
         let { title, remark } = this.state;
        
         return <div className="container">
                   <h1 className="title">{ title }</h1>
                   <div className="content">{ content }</div>
                   <div className="footer">
                       <button type="type" 
                           onClick={this.changeTitle}>
                           { remark }
                       </button>
                   </div>
                </div>
    }
}

Container.propType = {
    content: PropTypes.string.isRequired,
}

// 
ReactDOM.render(
    <Container content="hello world" />,
    document.body
);

```

##### JSX
    JSX可以看作JavaScript的拓展，，看起来有点像XML
    规则：
    遇到 HTML 标签（以 < 开头），就用 HTML 规则解析；遇到代码块（以 { 开头），就用 JavaScript 规则解析

##### ReactDOM.render()
    React 的最基本方法，用于将模板转为 HTML 语言，并插入指定的 DOM 节点

##### Component
    React 允许将代码封装成组件（component），然后像插入普通 HTML 标签一样，在网页中插入这个组件

##### Props
    组件对外数据接口

##### State
    组件对内数据接口

##### PropTypes
    用来验证组件实例的属性是否符合要求

##### 生命周期
    // 组件创建前调用
    componentWillMount()

    // 组件创建后调用
    componentDidMount()

    // 组件更新前调用
    componentWillUpdate(nextProps, nextProps)

    // 组件更新后调用
    componentDidUpdate(preProps, preState)

    // 判断是否重新渲染时调用
    shouldComponentUpdate(nextProps, nextState)

    // 已加载组件收到新的参数时调用
    componentWillReceiveProps(nextProps)

    // 组件卸载前调用
    componentWillUnmount()




### Redux
    Redux则是目前react配套的Flux模式的各种实现(其实现在两者的关系越来越模糊了)中最火的一个，在此基础上它引入了函数式编程、单一数据源、不可变数据、中间件等概念。一定程度来讲，redux是今年react生态甚至整个前端生态中影响最大的一个框架，它给整个前端技术栈引入了很多新成员，尽管这些概念可能在其他领域已经有了广泛的应用。虽然它们是否会在大规模的应用实践中被广大开发者认可还需要再检验，但至少给我们带来了一些新的思路。其中的单一数据源、不可变数据、中间件等思路目前来看还是非常有价值的，尤其是单一数据源跟不可变数据，很有可能在将来成为大型应用架构中的标配(目前来看至少在应用中构建Store层在当前的前端架构中是势在必行的)。单一数据源就好比在前端构建了一个集中式数据库，所有的数据存取操作对象都是它，不单如此它里面还实现了触发器，当有insert/update操作时它会对相应组件作rerender动作，这个在各组件之间有数据同步需求的场景下就非常有用了。

    Redux 中的函数传递及原理



    在 react-redux 中，数据的流向及对应的反应




### Webpack
    模块管理工具

    它同时支持commonjs和AMD规范（甚至混合的形式）；
    它可以打成一个完整的包，也可以分成多个部分，在运行时异步加载（可以减少第一次加载的时间）
    依赖在编译时即处理完毕，可以减少运行时包的大小；
    Loaders可以使文件在编译时得到预处理，这可以帮我们做很多事情，比如说模板的预编译，图片的base64处理；
    丰富的和可扩展的插件可以适应多变的需求。

