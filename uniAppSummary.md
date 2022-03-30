# 一、简介

## 1.1 规范

页面规范遵循Vue单文件组件规范

```vue
<template>
	<view> {{msg}} </view>
</template>

<script>
    export default({
        data() {
            return {
                msg: 'hello world'
            }
        }
    })
</script>

<style>
    view{
        background-color: red
    }
</style>
```

组件规范靠近小程序规范

```html
<template>
    <view> </view>
    <text> </text>
</template>
```

Api 靠近微信小程序规范

```javascript
uni.getLocation({
    type: 'wgs84',
    success: function(res) {
        console.log('当前位置的经度为：' + res.longitude)
        console.log('当前位置的纬度为：' + res.latitude)
    }
})
```

数据绑定及事件处理使用 Vue.js 规范

```vue
<template>
	<view @click="handleClick"> {{msg}} </view>
</template>

<script>
    export default({
        data() {
            return {
                msg: 'hello world'
            }
        },
        mothods: {
            handleClick() {
                this.msg = 'hola world'
            }
        }
    })
</script>
```

## 1.2 特色

### 1.2.1 条件编译

| 条件编译写法                                                 | 说明                                   |
| ------------------------------------------------------------ | -------------------------------------- |
| #ifdef APP-PLUS <br />需要条件编译的代码 <br />#endif        | 仅出现在 APP 平台下的代码              |
| #ifndef H5<br />需要条件编译的代码 <br />#endif              | 除了 H5 平台，其他平台均存在的代码     |
| #ifdef H5 \|\| MP-WEIXIN <br />需要条件编译的代码 <br />#endif | 在 H5 平台或者微信小程序平台存在的代码 |

### 1.2.2 App端的nvue开发

uni-app 中 App 端内置了一个基于 weex 改进的原生渲染引擎，提供了原生渲染能力。

在 App 端，如果使用 Vue 页面，则使用 webview 渲染；如果使用 nvue 页面 ( native vue )，则使用原生渲染。

### 1.2.3 HTML5+

uni-app 中 App 端内置了 HTML5+引擎，让 js 可以直接调用丰富的原生能力。

一些比较复杂的功能，可以直接调用 App 原生的插件来实现。

只能在 App 端使用，无法在 H5 和小程序中使用。

## 1.3 创建项目

方式一：Hbuilder创建 文件 => 新建 => 项目

方式二：vue-cli创建

```bash
vue create -p dcloudio/uni-preset-vue demo
```







