> 原文链接：https://www.taniarascia.com/getting-started-with-react/
# React辅导：概述和演练 
自从我开始学习JavaScript时，就听说过React，但是我要承认我看了一眼就被吓到了。我看到它像是一堆混合着JavaScript和思想的HTML，这不是我们要避免的吗？React有什么了不起的？

相反，我只专注于学习原生JavaScript并在专业环境里使用jQuery。在经历了几次失败的尝试后，我终于开始使用React，并明白为什么我可能要使用React，而不是原生JS或者JQuery。

我尝试把我学到所有东西精简成一个好的介绍分享给你，以下便是。

## 前提

在你开始玩React之前，这有一些需要事先知道的。如果你以前从没有使用过JavaScript或者DOM，举例来说，我会在使用React之前先熟悉它们

这里有我认为是使用React的前提条件。

- 基本熟悉HTML和CSS
- 对JavaScript和开发基本了解
- 基本理解DOM
- 熟悉ES6的语法和特性
- 全局安装Nodejs和Npm


## 目标

- 学习基本的React概念和相关术语，例如Babel，Webpack,JSX,组件，属性，状态和生命周期
- 构建一个非常简单的React应用用来演示上面的概念

这里有最终版本的源码和在线演示
- [View Source on Github](https://github.com/taniarascia/react-tutorial)
- [View Demo](https://taniarascia.github.io/react-tutorial/)

## 什么是React?
- React是最流行的JavaScript库之一，在Github上有超过100，000 stars
- React不是一个框架（不像Angular，过于顽固）
- React是Facebook创建的一个开源项目
- React常用来在前端构建UI
- React是一个MVC应用的视图层（Model,View,Controller）

React最重要的一个方面是你可以创建组件，这些组件类似可定制的，可重用的HTML元素，从而快速且高效的构建用户界面。React还使用了State和Props简化了数据的存储和处理。

我们将在文章中详细讨论这些内容，让我们开始吧

## 配置及安装
有一些设置React的方法，我将展示其中两种给你，这样你可以了解到它是如何工作的。

## 静态HTML文件
第一个方法不是建立React的流行方法并且在后面的教程中也不这样使用，但是如果你使用过类似JQuery的库，这将是熟悉和容易理解的。如果你不熟悉Webpack，Babel和Node.js，这将是最不可怕的入门方法

让我们从创建一个基本的Index.html文件开始。我们将在head里面读取3个CDN(资源)-React,React Dom和Babel。我们还将创建一个id为root的div，并在最后我们创建一个Script标签，你的自定会代码将在里面。


```html
<!-- index.html -->

<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />

    <title>Hello React!</title>

    <script src="https://unpkg.com/react@^16/umd/react.production.min.js"></script>
    <script src="https://unpkg.com/react-dom@16.13.0/umd/react-dom.production.min.js"></script>
    <script src="https://unpkg.com/babel-standalone@6.26.0/babel.js"></script>
  </head>

  <body>
    <div id="root"></div>

    <script type="text/babel">
      // React code will go here
    </script>
  </body>
</html>
```

在撰写本文的时候，我加载的是最新稳定版本的库。
- React —— React最顶级API
- React Dom —— 添加Dom具体的方法
- Babel - 一个JavaScript编译器，然我们能够在旧的浏览器中使用ES6

我们应用程序的入口点将是按照习惯命名的id为root的div元素。你将注意到script的脚本类型为text/babel，这让我们强制使用Babel。

现在，开始写我们的第一个React代码块。我们将使用ES6的类去创建一个叫做APP的React组件。


```html
<!-- index.html -->
class App extends React.Component {
  //...
}
```

现在我们将添加一个render()方法，在类组件中这是一个唯一且必须要有的方法，它常用来渲染DOM节点

```html
<!-- index.html -->
class App extends React.Component {
  render() {
      return (
          //...
      );
  }
}
```

return内部，我们将放一些看起来简单的html元素。注意我们在这里返回自负床，所以不要使用引号来包裹元素。这个叫做JSX，我们将会学习到更多关于它的。



```html
<!-- index.html -->
class App extends React.Component {
  render() {
    return <h1>Hello world!</h1>
  }
}
```

最后，我们将使用ReactDom的render()方法将创建的App类呈现到HTML中的 id为root的 div元素

```html
<!-- index.html -->
ReactDOM.render(<App />, document.getElementById('root'))
```

这里是我们index.html的全部代码

```html
<!-- index.html -->
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />

    <title>Hello React!</title>

    <script src="https://unpkg.com/react@16/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
    <script src="https://unpkg.com/babel-standalone@6.26.0/babel.js"></script>
  </head>

  <body>
    <div id="root"></div>

    <script type="text/babel">
      class App extends React.Component {
        render() {
          return <h1>Hello world!</h1>
        }
      }

      ReactDOM.render(<App />, document.getElementById('root'))
    </script>
  </body>
</html>
```

如果你现在在浏览器中预览你的index.html，你将会看见我们创建的h1标签已经渲染到DOM中。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200721212935771.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2R1YmlzbWlsZQ==,size_16,color_FFFFFF,t_70)



酷！现在你已经完成了它，你可以看见入门React并不是非常可怕的。它只是我们可以加载到html中的一些JavaScript辅助库。

我们这样做只是为了验尸，但是从这里开始我们将使用另一种方法：create React app(创建React应用)

## create React app(创建React应用)
前面的方法中，我在静态HTML页面中加载JavaScript库并匆忙渲染React和Babel，他并不是非常高效且不易于维护。

幸运的是，Face已经创建了Create React App，它会预先配置你需要构建的React App的所有东西。它将创建一个实时开发服务器，使用Webpack自动编译React，JSX和ES6，自动为CSS文件加前缀，并且自动用ESLint测试和警告代码中出现的错误。

使用create-react-app，在你的想要安装的目录下，打开终端上运行下面的代码。


```command
npx create-react-app react-tutorial
```

安装完成后，移动到新创建的目录并启动项目


```command
cd react-tutorial && npm start
```

一旦你运行了这个指令，一个新的包含你创建的React应用窗口将会在localhost:3000弹出

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200721213004954.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2R1YmlzbWlsZQ==,size_16,color_FFFFFF,t_70)


>  create React App 对于初学者和大型企业应用程序来说非常适合入门，但他不适合所有的工作流。你可以创建自己的webpack来建立React。

如果你观察项目结构，你可以看见一个/public和/src目录，以及常规的node_modules，.gitignore，README.md和package.json

在/public中，我们最重要的文件是index.html，它和我们之前创建的静态index.html非常相似—— 只有一个root div。这次，没有加载任何库或者脚本。/src目录将包含我们所有的React代码。

要查看环境是如何自动编译和更新你的react代码，在/src/app.js中找到类似这样的一行代码。



```
To get started, edit `src/App.js` and save to reload.
```

用其他文本将其替换。保存文件后，你将注意到localhost:3000编译并刷新新数据。

接着删除/src目录下的所有文件，并且我们创建自己的样板文件，而不会有任何多余的。我们只保留index.css和index.js。

对于index.css，我们仅复制粘贴[Primitive Css](https://taniarascia.github.io/primitive/css/main.css)到文件中。如果你想，你可以使用Bootstrap 或者任意一个你想要的css框架，或者啥也不用。我发现它很容易工作。

现在在index.js中，我们引入React,ReactDom和css文件

```javascript
// src/index.js

import React from 'react'
import ReactDOM from 'react-dom'
import './index.css'

```


让我们再一次创建App组件。之前我们仅有一个h1，但是现在我要添加了一个带有class的div元素。你将注意到我使用了className替代class。这是我们第一个提示，在这里写下的是JavaScript，而不是真正的HTML。


```javascript
// src/index.js
class App extends React.Component {
  render() {
    return (
      <div className="App">
        <h1>Hello, React!</h1>
      </div>
    )
  }
}
```

最终，我们像之前一样将App渲染到root



```javascript
// src/index.js
ReactDOM.render(<App />, document.getElementById('root'))

```

这里是我们index.js的全部代码。这一次我们将组件作为React的属性加载，所以我们不再需要额外继承React.Component。



```javascript
// src/index.js
import React, {Component} from 'react'
import ReactDOM from 'react-dom'
import './index.css'

class App extends Component {
  render() {
    return (
      <div className="App">
        <h1>Hello, React!</h1>
      </div>
    )
  }
}

ReactDOM.render(<App />, document.getElementById('root'))
```

如果你返回localhost:3000，和之前一样，你将看到 “Hello，React”。我们现在有了一个React应用程序。

## React Developer Tool(React开发者工具)

这里有一个叫做React Developer Tool的扩展，它们将让你在使用React时的更加轻松。下载[React DevTools for Chrome](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi)，或者其他你更喜欢的浏览器上运行它。

安装完后，当你打开开发工具时，你将看到React标签项。点击它，你将可以在编写组件时检查它们了。你可以去Elements(元素)标签项看实际的Dom输出。现在看起来可能不是一个好的解决，但是随着app越来越复杂，它将越来越有必要使用。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200721213035961.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2R1YmlzbWlsZQ==,size_16,color_FFFFFF,t_70)



现在我们有了所有工具和设置，我们可以开始真正使用React。

## JSX：JavaScript + XML

如你所见，我们已经在React代码中使用过一个看起来很像HTML的代码，那是它不是html代码，它是JSX，它代表着JavaScript XML。

使用JSX，我们可以写出像HTML的代码，而且我们可以创建并使用自己的像XML的标签。下面是赋值给一个变量的JSX。



```javascript
//JSX
const heading = <h1 className="site-heading">Hello, React</h1>
```

在编写React时，并不是必须要使用JSX。在引擎中，他将运行CreateElement来获取标签，包含属性的对象，子组件并渲染相同的信息。下面的代码和上面的JSX有着同样的输出。


```javascript
//No JSX
const heading = React.createElement('h1', {className: 'site-heading'}, 'Hello, React!')
```

JSX特别接近于JavaScript，而不是HTML，因此在编写它的时有一些关键的区别需要注意：
- 使用className替代class添加css类，因为class是JavaScript的保留关键词
- 在JSX中的属性和方法使用小驼峰命名 —— onclick 将会变成 onClick
- 单标签(闭标签)必须使用斜杠(/)结束 —— <img />

JavaScript表达式可以在大括号中嵌入JSX，包括变量、方法和属性。



```javascript
const name = 'Tania'
const heading = <h1>Hello, {name}</h1>
```


JSX比使用原生JavaScript创建和添加大量元素更容易编写和理解，这也是人们如此喜欢React的原因之一。


## Components(组件)

目前欸之，我们只创建了一个组件 —— App组件。在React中几乎所有东西都由组件构成，这些可以是类组件或者简单组件。


大多数React应用都有许多组件，并且所有东西都被加载到主App组件中。组件经常要获取它们拥有的组件，所以我们按照那样来修改我们的项目。

从index.js中移除App类，它看起来像是这样：



```javascript
//src/index.js
import React from 'react'
import ReactDOM from 'react-dom'
import App from './App'
import './index.css'

ReactDOM.render(<App />, document.getElementById('root'))
```

我们创建一个新的文件叫App.js，并将组件放在这里。


```javascript
//src/app.js

import React, {Component} from 'react'

class App extends Component {
  render() {
    return (
      <div className="App">
        <h1>Hello, React!</h1>
      </div>
    )
  }
}

export default App

```

我们到导出了App组件并把它加载到index.js中。将组件分离到文件中并不是强制的，但是如果你不这么做，应用将开始变得笨拙且失控。


## Class Components(类组件)

让我们创建另一个组件。我们将要创建一个表格。新建Table.js并用以下代码填充它。



```javascript
//src/Table.js
import React, {Component} from 'react'

class Table extends Component {
  render() {
    return (
      <table>
        <thead>
          <tr>
            <th>Name</th>
            <th>Job</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Charlie</td>
            <td>Janitor</td>
          </tr>
          <tr>
            <td>Mac</td>
            <td>Bouncer</td>
          </tr>
          <tr>
            <td>Dee</td>
            <td>Aspiring actress</td>
          </tr>
          <tr>
            <td>Dennis</td>
            <td>Bartender</td>
          </tr>
        </tbody>
      </table>
    )
  }
}

export default Table

```

我们创建的这个组件是一个自定义的类组件。我们用大驼峰写法来区分自定义组件和常规的html元素。回到App.js，我们要加载Table，首先要引入它。


```javascript
//src/app.js
import Table from './Table'
```

然后将它加载到app的render()函数中，之前这里我们有“Hello, React!”。我还改变了外部容器的类。


```javascript
//src/App.js
import React, {Component} from 'react'
import Table from './Table'

class App extends Component {
  render() {
    return (
      <div className="container">
        <Table />
      </div>
    )
  }
}

export default App
```


如果你检查了你的生产环境，你将会看到被加载的Table。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200721213058750.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2R1YmlzbWlsZQ==,size_16,color_FFFFFF,t_70)


现在我们已经知道什么是自定义类组件了。我们可以不断复用这个组件。然而，由于数据是硬编码进去的（写死在里面的），所以目前还不是非常有用。

## Simple Components（简单组件）

在React中的另一种组件是简单组件，他是一个函数。这个组件不适用class关键字。让我们使用table创建两个简单组件 —— 一个tabel header，一个table body。

我们将使用ES6的箭头函数来创建这些简单组件。首先，这是table header。


```javascript
// src/Table.js
const TableHeader = () => {
  return (
    <thead>
      <tr>
        <th>Name</th>
        <th>Job</th>
      </tr>
    </thead>
  )
}
```


然后这是 table body

```javascript
// src/Table.js
const TableBody = () => {
  return (
    <tbody>
      <tr>
        <td>Charlie</td>
        <td>Janitor</td>
      </tr>
      <tr>
        <td>Mac</td>
        <td>Bouncer</td>
      </tr>
      <tr>
        <td>Dee</td>
        <td>Aspiring actress</td>
      </tr>
      <tr>
        <td>Dennis</td>
        <td>Bartender</td>
      </tr>
    </tbody>
  )
}
```

现在我们的Table文件将看起来像这样子。注意TableHeader和TableBody组件都在通过一个文件里，并且被Tabel类组件使用。


```javascript
// src/Table.js
const TableHeader = () => {
  return (
    <thead>
      <tr>
        <th>Name</th>
        <th>Job</th>
      </tr>
    </thead>
  )
}
```


然后这是 table body

```javascript
// src/Table.js
const TableHeader = () => { ... }
const TableBody = () => { ... }

class Table extends Component {
  render() {
    return (
      <table>
        <TableHeader />
        <TableBody />
      </table>
    )
  }
}
```

一切事物呈现的跟之前一样。如你所见，组件可以嵌套在其他组件中，并且简单组件和类组件可以混合使用。

> 类组件必须包含render()函数，并且只能返回一个父元素。

总的来说，让我们比较一下简单组件和类组件。


```javascript
// Simple Component (简单组件)
const SimpleComponent = () => {
  return <div>Example</div>
}
```


```javascript
// Class  Component (类组件)
class ClassComponent extends Component {
  render() {
    return <div>Example</div>
  }
}
```

注意：如果return返回值包含在一行内，它可以不需要括号。

## Props(属性)
现在，我们有了一个非常酷的Table组件，但是数据是硬编码的（写死的）。React中重要特点之一是如何处理数据，它用被称为props的属性和state来处理数据。首先我们先关注于使用props处理数据。

首先，从TableBody组件移除所有数据。


```javascript
//src/Table.js
const TableBody = () => {
  return <tbody />
}
```

然后移动所有数据到一个数组对象中，就像我们引入了一个基于JSON的API。我们必须在render()里创建这个数组。



```javascript
//src/App.js
class App extends Component {
  render() {
    const characters = [
      {
        name: 'Charlie',
        job: 'Janitor',
      },
      {
        name: 'Mac',
        job: 'Bouncer',
      },
      {
        name: 'Dee',
        job: 'Aspring actress',
      },
      {
        name: 'Dennis',
        job: 'Bartender',
      },
    ]

    return (
      <div className="container">
        <Table />
      </div>
    )
  }
}
```



现在，我们将要把数据传递给带有属性的自组件（Table），类似于你可以使用data-属性传递数据。我们可以调用我们想用的任意属性，只要他不是一个内置关键词，因此我将使用characterData。我传递的数据是characters变量，并且我在它两边加上大括号，因为它是一个JavaScript表达式


```javascript
// src/App.js
return (
  <div className="container">
    <Table characterData={characters} />
  </div>
)
```

现在数据已经传递到了Table，我们必须在另外一边访问它


```javascript
// src/Table.js

class Table extends Component {
  render() {
    const {characterData} = this.props

    return (
      <table>
        <TableHeader />
        <TableBody characterData={characterData} />
      </table>
    )
  }
}
```

如果你打开React开发工具并检查Table组件，你将会看见在属性中看到数组数据。存在这里的数据被称为虚拟DOM，它是一种快速且高效地将数据与实际DOM同步的方法。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200721213128785.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2R1YmlzbWlsZQ==,size_16,color_FFFFFF,t_70)


不过，这些数据还没有在实际的Dom里。在Table中，我们可以通过this.props访问所有属性。我们只有传递了一个属性，所以我们将要使用this.props.characterData 来检索数据。

我将使用ES6简写属性创建包含this.props.characterData的变量。


```
const {characterData} = this.props
```

由于我们的Table组件实际由两个较小的简单组件组成，我们再一次通过props将其传递到TableBody组件中。



```javascript
// src/Table.js

class Table extends Component {
  render() {
    const {characterData} = this.props

    return (
      <table>
        <TableHeader />
        <TableBody characterData={characterData} />
      </table>
    )
  }
}
```

现在，TableBody没有携带一个参数并返回单个标签

```javascript
// src/Table.js
const TableBody = () => {
  return <tbody />
}
```

我们将传递props作为参数，和[通过遍历数组](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)为数组中每个对象返回一个表行。这个映射将包含在rows变量，它会作为表达式返回。


```javascript
// src/Table.js
const TableBody = (props) => {
  const rows = props.characterData.map((row, index) => {
    return (
      <tr key={index}>
        <td>{row.name}</td>
        <td>{row.job}</td>
      </tr>
    )
  })

  return <tbody>{rows}</tbody>
}
```

如果你浏览应用程序的前端，所有的数据都正在加载。

你会注意到我已经给每个表行添加了一个键索引，你在React中创建列表时应该使用keys，因为它们帮助你能识别每个列表项。当我们想要操作列表项时，就会明白这将是有必要的。

props是传递已有数据到React组建的高效方法，然而组件不能直接修改Props —— 它们只是只读的。在下一节中，我们将在React中学习如何使用状态进一步控制数据的处理。

## State(状态)
现在，我们要存储我们的character数据在一个数组变量里面，将其作为props传递。这是一个好的开始，但是想像一下，如果我们想要从数组里面删除数组项。使用Props，我们就有一个单向的数据流，但是我们可以从组件里更新私有状态。

你可以把state考虑作为任意数据，这个数据可以被保存到和修改且没有必要添加到数据库中 —— 例如，在确认你的购买之前，你可以从购物车中添加和删除。

首先，我们创建一个state对象



```javascript
// src/App.js
class App extends Component {
  state = {}
}

```

这个对象将包含你想要存储在状态里的所有属性。对于我们而言，那就是characters。


```javascript
// src/App.js
class App extends Component {
  state = {
    characters: [],
  }
}
```

移动整个数组对象到我们新创建的state.characters。


```javascript
// src/App.js
class App extends Component {
  state = {
    characters: [
      {
        name: 'Charlie',
        // the rest of the data
      },
    ],
  }
}
```

我们的数据被正式保存在state里面。由于我们想要能够从表格里面移除字符，我们将在父类APp中创建一个removeCharacter方法。

为了找到这个State，我们使用this.state.characters，这和之前一样使用的ES6方法一样。为了更新State，我们将使用this.setState()，一个内置方法来操作state。我们将基于传递的index(索引)[过滤数组](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)，并返回新的数组。

> 你必须使用this.setState()来更新数组。简单的赋予一个新值给this.state.property将不起作用。


```javascript
// src/App.js

removeCharacter = (index) => {
  const {characters} = this.state

  this.setState({
    characters: characters.filter((character, i) => {
      return i !== index
    }),
  })
}

```

filter 不会发生变化，而是创建一个新数组，并且在JavaScript中这是修改数组的好方法。这个特定的方法是测试一个索引相较于数组内的所有索引，并返回除传递索引之外的所有索引。

现在，我们必须将函数传递给组件，并且在每个可以出发函数的字符旁边渲染一个按钮。我们将removeCharacter函数作为一个Prop传递给Table组件。


```javascript
// src/App.js
render() {
  const { characters } = this.state

  return (
    <div className="container">
      <Table characterData={characters} removeCharacter={this.removeCharacter} />
    </div>
  )
}
```

由于我们将它一直从Table传递到TableBody，我们必须再一次将它作为prop传递，就像我们刚刚操作character数据一样。

另外，由于在我们的项目中只有App和Form组件具有自己的状态，因此最好将Table从当前的类组件转换成简单组件。


```javascript
// src/Table.js
const Table = (props) => {
  const {characterData, removeCharacter} = props

  return (
    <table>
      <TableHeader />
      <TableBody characterData={characterData} removeCharacter={removeCharacter} />
    </table>
  )
}
```

这就是我们在removeCharacter()函数中定义的索引的位置。在TableBody组件中，我们将 key(键)/index(索引)作为参数传递，然后filter(过滤)函数就知道哪个列表项需要移除。我们将创建一个绑定了onClick的按钮并传递它。


```javascript
// src/Table.js

<tr key={index}>
  <td>{row.name}</td>
  <td>{row.job}</td>
  <td>
    <button onClick={() => props.removeCharacter(index)}>Delete</button>
  </td>
</tr>
```

> onClick函数必须传递一个返回removeCharacter() 的函数，否则它将尝试自动运行。

太棒了。现在我们有了一个删除按钮，而且我们可以通过删除character来修改我们的State。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200721213208415.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2R1YmlzbWlsZQ==,size_16,color_FFFFFF,t_70)


我删除了MAC

现在你应该明白如何初始化state，并且如何修改它了。

## Submitting Form Data（提交表单数据）

现在我们的数据存储在state（状态）中，我们可以从state中移除任意数据项。但是，如果我们想要添加新的数据到state怎么办？ 在现实世界中的应用程序，你更有可能从空的state开始并向其添加数据，比如一个待办事项清单或者购物车。


首先，我们从state.characters中移除所有硬编码数据，我们会通过表单更新它。


```javascript
// src/App.js

class App extends Component {
  state = {
    characters: [],
  }
}
```

现在让我们在一个叫做Form.js的新文件中创建一个Form组件。

我们将设Form中的state初始值为带有空属性的对象，并将其初始state赋值给this.state。

```javascript
// src/Form.js

import React, {Component} from 'react'

class Form extends Component {
  initialState = {
    name: '',
    job: '',
  }

  state = this.initialState
}
```

> 以前，必须在React类组件上包含constructor()，但现在不需要了

这个表单的目标是每当表单中的字段发生改变时，更新表单的State（状态），并且当我们提交时，所有数据将传递给app的state，之后将修改Table。

首先，我们将创建函数，它将在每次对input(输入框)进行更改时运行。event(时间)将被传递，我们设置表单的状态，使之具有name(key)和value


```javascript
// src/Form.js
handleChange = (event) => {
  const {name, value} = event.target

  this.setState({
    [name]: value,
  })
}

```


让我们在提交表单前完成它。在渲染时，我们从state中获取两个属性，并将其作为值赋值给对应的表单建。我们将运行handleChange()方法作为input的onChange属性，最后我们将会导出Form组件。

```javascript
// src/Form.js
render() {
  const { name, job } = this.state;

  return (
    <form>
      <label htmlFor="name">Name</label>
      <input
        type="text"
        name="name"
        id="name"
        value={name}
        onChange={this.handleChange} />
      <label htmlFor="job">Job</label>
      <input
        type="text"
        name="job"
        id="job"
        value={job}
        onChange={this.handleChange} />
    </form>
  );
}

export default Form;

```


在App.js中，我们可以将表单渲染到表格下面。


```javascript
// src/App.js
import Form from './Form'

```

```javascript
// src/App.js
return (
  <div className="container">
    <Table characterData={characters} removeCharacter={this.removeCharacter} />
    <Form />
  </div>
)

```

现在如果我们去应用的前端，我们可以看到一个尚未提交的表单。更新一些字段后，你将看将表单的本地状态（state）正在更新。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200721213254450.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2R1YmlzbWlsZQ==,size_16,color_FFFFFF,t_70)


太酷了。最后允许我们实际地提交表单数据并更新父级状态（state）。我们将在app里面创建一个叫handleSubmit() 的函数，它将通过获取现有的this.state.characters来更新状态，并且使用[ES6的展开运算符](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax)添加新的character参数


```javascript
// src/App.js
handleSubmit = (character) => {
  this.setState({characters: [...this.state.characters, character]})
}

```

让我们在Form组件中确保作为一个参数传递。


```javascript
<Form handleSubmit={this.handleSubmit} />
```

现在在Form中，我们创建了一个叫做submitForm()的函数，将通过调用这个函数，将表单状态作为前面定义的字符参数传递。他还将state重置为初始状态，确保在提交后清除表单。


```javascript
// src/Form.js

submitForm = () => {
  this.props.handleSubmit(this.state)
  this.setState(this.initialState)
}
```

最后，我们在表单中添加一个提交按钮用来提交表单。由于我们不能使用标准提交功能，所以我们使用onClick替代onSubmit来提交。单击将调用我们刚刚创建的submitForm。


```javascript
// src/Form.js
<input type="button" value="Submit" onClick={this.submitForm} />
```

 这就是React!。这个应用已经完成了。我们可创建、添加并且移除表格中的用户。由于Table和TableBody已经从State中获取到值，它将正常显示.

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200721213317581.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2R1YmlzbWlsZQ==,size_16,color_FFFFFF,t_70)


 如果你在旅途中迷失了方向，你可以在[github](https://github.com/taniarascia/react-tutorial)上查看完整的源代码。


## Pulling in API Data （获取API中的数据）

React的一个非常常见的用法就是从API中拉取数据。如果你不熟悉API是什么或者如何连接它，那么我推荐你阅读
[JavaScript怎样连接API](https://www.taniarascia.com/how-to-connect-to-an-api-with-javascript/)，这能让你理解API是什么，并如何使用原生javaScript使用它。

作为一个小测试，我们可以创建一个新的Api.js文件，并在这里创建一个新的App。我们可以测试一个公共的Api是[维基百科的API](https://en.wikipedia.org/w/api.php)，我还有一个[URL端点](https://en.wikipedia.org/w/api.php?action=opensearch&search=Seona+Dancing&format=json&origin=*)是用来随机搜索的。你可以进入链接查看API——请确保你在浏览器里安装了[JSONView](https://chrome.google.com/webstore/detail/jsonview/chklaanhfefbnpoihckbnefhakgolnmc)

我们将使用[JavaScript内置的Fetch](https://www.taniarascia.com/how-to-use-the-javascript-fetch-api-to-get-json-data/)方法来从url端点获取数据并展示它。你可以通过更改index.js-import App from './Api';中的url来切换我们创建的应用和这个测试文件。

我不想一行一行解释，所以我们已经学习了关于创建一个组件、渲染、并且遍历传递的state数组。现在这个代码有一个新的方面是componentDidMount()，一个React的生命周期方法。
Lifecycle（生命周期）是在React中调用方法的顺序。Mounting是指正在插入Dom中的项。

当我们从API中拉取数据，我希望使用componentDidMount，因为我们希望在引入数据前，确保组件已经渲染Dom。在下面的片段中，你将看到我们如何从维基百科API中引入书，并展示到页面上的。


```javascript
// Api.js
import React, {Component} from 'react'

class App extends Component {
  state = {
    data: [],
  }

  // Code is invoked after the component is mounted/inserted into the DOM tree.
  componentDidMount() {
    const url =
      'https://en.wikipedia.org/w/api.php?action=opensearch&search=Seona+Dancing&format=json&origin=*'

    fetch(url)
      .then((result) => result.json())
      .then((result) => {
        this.setState({
          data: result,
        })
      })
  }

  render() {
    const {data} = this.state

    const result = data.map((entry, index) => {
      return <li key={index}>{entry}</li>
    })

    return <ul>{result}</ul>
  }
}

export default App

```

在本地服务器中保存并运行此文件，你见看到显示在Dom中的维基百科数据。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200721213341881.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2R1YmlzbWlsZQ==,size_16,color_FFFFFF,t_70)


还有其他的生命周期方法，但是对它们的讨论超出了本文的范围。你可以在这里阅读更多[关于React组件内容](https://reactjs.org/docs/react-component.html)

**维基百科的查询选择可能不是随机的，这可能是我们2005年带头写的一篇文章。*

## Building and Deploying a React App (编译并部署React应用)

到目前为止，我们所做的一切都是在开发环境完成的。我们一直在编译，热重载和更新。对于生产环境，我们希望加载静态文件 —— 不包含源代码。我们可以通过构建并部署它来实现这一点。

现在，如果你想要编译所有React代码，并将其放在根目录下某个地方，你需要运行下面一行代码：

```
npm run build
```

这将创建build文件夹并且将你的应用包含在里面。将该文件夹的内容放到任何地方，就完成了。

我们还可以再更进一步，用npm为我们部署。我们去构建Github页面，因此你必须[熟悉Git](https://www.taniarascia.com/getting-started-with-git/)并且从github上获取你的代码。

请确保你退出了你本地的React环境，即代码没有正在运行。首先我们添加一个Homepage字段到packge.json，其中包含我们希望应用程序运行的url。


```javascript
// package.json

"homepage": "https://taniarascia.github.io/react-tutorial",
```

我们再添加这两行到scripts属性中。

```javascript
// package.json

"scripts": {
  // ...
  "predeploy": "npm run build",
  "deploy": "gh-pages -d build"
}
```

在你的项目里，将gh-pages添加到开发依赖库里面。

```
npm install --save-dev gh-pages
```

我们将创建build文件夹，它将有所有的编译好的静态文件。

```
npm run build
```

最后我们将部署到gh-pages

```
npm run deploy
```

大功告成。应用已经在链接[https://taniarascia.github.io/react-tutorial](https://taniarascia.github.io/react-tutorial)里了。


## 结论

希望这篇文章能给你很好的介绍了React、简单/类组件、state、props，处理表单数据，从API中获取数据和部署应用程序。关于React还有许多要学习和实践的事情，但是我希望你有信息去钻研和玩React。

- [查看Github源码](https://github.com/taniarascia/react-tutorial)
- [查看项目](https://taniarascia.github.io/react-tutorial/)

如果有什么不明白的地方，或者你想在本文或后续文章中看到什么，请让我知道。

---
老规矩写的不清晰的地方，可以指出，我会不定时更新和修改。一起加油.

所有的伟大，都来自于一个勇敢的开始。