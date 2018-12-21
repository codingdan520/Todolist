# Todolist制作
## 实现思路
1. 将整个todolist分为三个部分，输入部分(todo.vue)，展示部分(item.vue),执行部分(tabs.vue)
2. 在todo.vue中定义一个空数组todos，在输入框中通过绑定keyup事件，向空数组中传入内容
3. 在item子组件中，通过v-for方式循环输出todos里面的内容
4. item.vue中分为三个部分type="checkbox",内容和删除按钮
5. 在tabs.vue中分为三个部分，左(显示未完成的项目个数)，中(筛选全部，未完成，完成按钮)，右(清除全部)

## 打包时遇到的问题(页面不加载)？
+ 进入dist目录下的index.html会报错：Failed to load resource: net::ERR_FILE_NOT_FOUND
### 解决办法
1. 进入config目录下的index.js文件，将build对象中的 assetsPublicPath: '/' ==> assetsPublicPath: './';

## 打包时遇到的问题(页面不加载和图片不加载)？
+ 进入dist目录下的index.html会报错：Failed to load resource: net::ERR_FILE_NOT_FOUND
### 解决办法
1. 进入build目录下的utils.js文件，在 fallback: 'vue-style-loader',后面添加 publicPath: '../../',
        
