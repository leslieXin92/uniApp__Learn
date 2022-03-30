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



