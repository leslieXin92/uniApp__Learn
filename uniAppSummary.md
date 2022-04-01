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
        methods: {
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

## 1.4 项目目录

<img src="https://raw.githubusercontent.com/leslieXin92/picGo/master/img/202203301654742.png" style="zoom:80%;" />

# 二、基本语法

## 2.1 模板语法

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
        methods: {
            handleClick() {
                this.msg = 'hola world'
            }
        }
    })
</script>
```

## 2.2 数据绑定

```vue
<template>
	<view>
		<image :src="imgPath" mode="aspectFit" />
		<input type="text" v-model="msg" />
		<view> 此时data中msg的值为：{{ msg }} </view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			imgPath: '../../static/logo.png',
			msg: 'yahoo'
		};
	}
};
</script>

<style>
* {
	margin: 10px;
}
image {
	width: 50%;
}
input {
	width: 50%;
	outline: 2px solid #007aff;
}
</style>

```

## 2.3 条件渲染

```vue
<template>
	<view>
		<label>
			<checkbox :checked="flag" @click="handleChangeStatus" />
		</label>
		
		<!-- v-if -->
		<view v-if="flag"> 此时data中的flag为true </view>
		<view v-else> 此时data中的flag为false </view>
		
		<!-- v-show -->
		<view v-show="flag"> 此时data中的flag为true </view>
		<view v-show="!flag"> 此时data中的flag为false </view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				status: true,
				flag: false
			}
		},
		methods: {
			handleChangeStatus(){
				this.flag = !this.flag
			}
		}
	}
</script>
```

## 2.4 列表渲染

```vue
<template>
	<view>
		<view v-for="(item, index) in list" :key="item.id"> 
			{{index}} : {{ item.name }} 
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			list: [{
				id:'001',
				name:'uni-App'
			},{
				id:'002',
				name:'TypeScript'
			},{
				id:'003',
				name:'Vue3'
			}]
		}
	}
}
</script>
```

## 2.5 事件绑定

```vue
<template>
	<view class="box">
		<view class="father" @click="handleClickFather">
			<view class="son" @click.stop="handleClickSon" />
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {}
		},
		methods: {
			handleClickFather(){
				console.log('father被点击了！')
			},
			handleClickSon(){
				console.log('son被点击了！')
			}
		}
	}
</script>

<style>
.father{
	display: flex;
	justify-content: center;
	align-items: center;
	width: 200px;
	height: 200px;
	margin: 20px auto;
	background-color: #007AFF;
}
.son{
	width: 100px;
	height: 100px;
	background-color: #4CD964;
}
</style>
```

## 2.6 基础组件

```html
<template>
	<view class="box">
		<view> 我是view组件 </view>

		<scroll-view scroll-y scroll-x>
			<view v-for="i in 10"> 我是scroll-view组件 </view>
		</scroll-view>

		<text> 我是text组件 </text>

		<swiper indicator-dots autoplay>
			<swiper-item>
				<view> swiper-item1 </view>
			</swiper-item>
			<swiper-item>
				<view> swiper-item2 </view>
			</swiper-item>
			<swiper-item>
				<view> swiper-item3 </view>
			</swiper-item>
		</swiper>
	</view>
</template>
```

更多基础组件：<a href="https://uniapp.dcloud.net.cn/component/" style="text-decoration:none"> 网址 </a>

## 2.7 自定义组件

hello 组件：

```vue
<template>
	<text :style="{ color }"> hello </text>
</template>

<script>
export default {
	name:"hello",
	props:{
		color: {
			type: String,
			default: 'blue'
		}
	}
}
</script>
```

world 组件：

```vue
<template>
	<text :style="{ color }"> world </text>
</template>

<script>
export default {
	name:"world",
	props: {
		color: {
			type: String,
			default: 'blue'
		}
	}
}
</script>
```

父组件：

```html
<template>
	<view>
		<hello color="red" />
		<world />
	</view>
</template>
```

## 2.7 常用Api

设置标题：

```javascript
uni.setNavigationBarTitle({
    title: 'new title'
})
```

交互反馈：

```javascript
uni.showToast({
    title:'加载中',
    icon: 'loading'
})
```

页面跳转：

```javascript
// navigateTo
uni.navigateTo({
	url: 'test?id=1&name=yahoo'
})

// redirectTo
uni.redirectTo({
	url: 'test?id=1'
})

// navigateBack
uni.navigateBack({
	delta: 1
})

// reLaunch
uni.reLaunch({
	url: 'test?id=1'
})

// switchTab
uni.switchTab({
	url: '/pages/index/index'
})
```

更多Api：<a href="https://uniapp.dcloud.net.cn/api/" style="text-decoration:none"> 网址 </a>

## 2.8 生命周期

### 2.81 应用生命周期

应用生命周期仅可在 App.vue 中监听，在其它页面5监听无效。

|       钩子        |                     说明                      |
| :---------------: | :-------------------------------------------: |
|     onLaunch      | 当 uni-app 初始化完成时触发（全局只触发一次） |
|      onShow       |     当 uni-app 启动，或从后台进入前台显示     |
|      onHide       |        当 uni-app 从前台进入后台时触发        |
|      onError      |             当 uni-app 报错时触发             |
| onUniNviewMessage |        对 nvue 页面发送的数据进行监听         |

### 2.8.2 页面生命周期

|                钩子                 |                    说明                    |
| :---------------------------------: | :----------------------------------------: |
|               onLoad                |   监听页面加载，参数为上个页面传递的数据   |
|               onShow                | 监听页面显示，页面每次出现在屏幕上都会触发 |
|               onReady               |            监听页面初次渲染完成            |
|               onHide                |                监听页面隐藏                |
|              onUnload               |                监听页面卸载                |
|              onResize               |              监听窗口尺寸变化              |
|          onPullDownRefresh          |              监听用户下拉动作              |
|            onReachBottom            |              监听页面上拉到底              |
|            onTabItemTap             |              点击 tab 时触发               |
|          onShareAppMessage          |             用户点击右上角分享             |
|            onPageScroll             |                监听页面滚动                |
|      onNavigationBarButtonTap       |         监听原生标题栏按钮点击事件         |
|             onBackPress             |                监听页面返回                |
|  onNavigationBarSearchInputChanged  |  监听原生标题栏搜索输入框输入内容改变事件  |
| onNavigationBarSearchInputConfirmed |      监听原生标题栏搜索输入框搜索事件      |
|   onNavigationBarSearchInputClick   |      监听原生标题栏搜索输入框点击事件      |

tips：

1.  onPullDownRefresh：下拉刷新，需要在 `pages.json` 里配置 enablePullDownRefresh 为 true，当处理完数据刷新后，uni.stopPullDownRefrsh 可以停止当前页面的下拉刷新。enablePullDownRefresh 设置为 false 可以禁止改页面下拉刷新。
2.  onReachBottom：上拉加载，可以在 `pages.json` 里配置触发距离 onReachBottomDistance；若使用 scroll-view 组件导致页面没有滚动，则不会触发触底事件。

### 2.8.3 组件生命周期

| 钩子 | 说明 |
| ---- | ---- |
|      |      |
|      |      |
|      |      |
|      |      |
|      |      |
|      |      |
|      |      |
|      |      |





