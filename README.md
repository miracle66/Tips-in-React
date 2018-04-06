# Swiper-in-React
手把手教你在 react 中使用 Swiper 4 做轮播图


## 为啥要写这个东西
项目之前是用的 jq，现在打算用 React 重构，由于原项目已经引用了 Swpier 组件，故自然而然重构项目的时候也就考虑到怎么在 React 中使用这个组件。<br>
由于 Swiper 官方文档并没有针对 React 的例子，而我又是个 React 新手，一下子懵逼，不知道如何使用，现在经过摸索之后，把相关经验总结并分享出来，供后来者参考。

## 搭建 React 环境
1. 安装脚手架 <br>
`npm install -g create-react-app`
2. 搭建项目 swiper-react 项目名字不能大写 <br>
`create-react-app swiper-react`

## 运行环境
在项目目录结构，运行以下命令：

`npm start`

在开发模式下调试项目，将会自动打开本地服务器 [http://localhost:3000](http://localhost:3000)

此时，代码的变动将会实时反映到浏览器中

`npm run build`

在文件夹 `build` 中打包用于生产环境的代码

## 安装 Swiper

`npm install --save swiper`

## 编写 Swiper 组件

1. 首先引入 Swiper 以及样式

``` javascript
import Swiper from 'swiper'

import 'swiper/dist/css/swiper.min.css'
```
2. 在组件挂载完毕的时候生成 Swiper 对象

``` javascript
componentDidMount() {
    new Swiper(this.swiperID, {
        pagination: {
            el: this.paginateID,
        },
    });
}
```

`this.swiperID` 和 `this.paginateID` 本来应该是 HTML 元素或者相应的元素选择器字符串，如 '#swiper' <br>
在 React 中我用了 ref 方法去引用已到达引用元素的效果。

3. 在 React 的 render 方法构造 html 结构，注意 ref 的引用

``` javascript
render() {
    const items = this.renderList()
    return (
        <div className="wxchat-banner">
            <section className="new_custom swiper-container index_tab_con" ref={self => this.swiperID = self}>
                <ul className="swiper-wrapper">
                    {items}
                </ul>
                <div className="swiper-pagination banner-pagination" ref={self => this.paginateID = self}></div>
            </section>
        </div>
    )
}
```
## 接下来引用插件的方法如下 <br>

`ReactDOM.render(<Swiper />, document.getElementById('root'))`

以上就是作为一个展示性组件如何引入 Swiper 并在 React 中实现轮播图的代码。



