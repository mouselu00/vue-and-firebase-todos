# Vue + Firebase

这是一个参考`ReactJS`的一个App编译成`VueJS`的自我练习专案。为了让自己更了解`Vue`+ `firebase`建构App的知识,而实做是最快上手的。

Source: [Let's Code Along: Noted](https://www.youtube.com/playlist?list=PL57atfCFqj2g46GOvNNU1cnBUv3_X-uot)
[DEMO](http://mouselu00.github.io/vue-and-firebase-todos)

## 功能
* CRUD
  * title
  * date
  * content
* Sign In/Out

## 遇到的事
1. `EventBus`虽然让兄弟元件(brothe component)带来的通讯的便利性同时也带来了维护问题和追踪问题
2. 如果想要让`eslint`在耨一个文件停止诊断语法,在文件上加上`/* eslint-disable */`
3. 不知道为什么`vue`的`methdos`不能使用`for-in`
4. `firebase`的功能很多,包裹验证等等的，能使用第三方库`vuefire`
5. `prop`的命名规则需要注意和使用有意义的方式命名

## 补充
这个App还有很多可以强化的地方：
* 输入验证和过滤
* 性能优化
* UI/UX优化
* 代码结构
* 功能简化

不过主要的还是`firebase` + `vue`的初次接触与学习。
