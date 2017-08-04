# Vue + Firebase

这是一个参考`ReactJS`的一个App编译成`VueJS`的自我练习专案。为了让自己更了解`Vue`+ `firebase`建构App的知识,而实做是最快上手的。

Source: [Let's Code Along: Noted](https://www.youtube.com/playlist?list=PL57atfCFqj2g46GOvNNU1cnBUv3_X-uot)
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
