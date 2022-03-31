<template>
	<view class="box">
		<button type="primary" @click="skipTemplateSyntax"> 模板语法 </button>
		<button type="primary" @click="skipDataBinding"> 数据绑定 </button>
		<button type="primary" @click="skipConditionalRender"> 条件渲染 </button>
		<button type="primary" @click="skipListRender"> 列表渲染 </button>
		<button type="primary" @click="skipEventBinding"> 事件绑定 </button>
		<button type="primary" @click="skipComponents"> 基础组件 </button>
		<button type="primary" @click="skipCustomComponents"> 自定义组件 </button>
	</view>

</template>

<script>
export default {
	data() {
		return {}
	},
	methods:{
		// 模板语法
		skipTemplateSyntax(){
			uni.navigateTo({
				url:'/pages/templateSyntax/templateSyntax'
			})
		},
		// 数据绑定
		skipDataBinding(){
			uni.navigateTo({
				url:'/pages/dataBinding/dataBinding'
			})
		},
		// 条件渲染
		skipConditionalRender(){
			uni.navigateTo({
				url:'/pages/conditionalRender/conditionalRender'
			})
		},
		// 列表渲染
		skipListRender(){
			uni.navigateTo({
				url:'/pages/listRender/listRender'
			})
		},
		// 列表渲染
		skipEventBinding(){
			uni.navigateTo({
				url:'/pages/eventBinding/eventBinding'
			})
		},
		// 基础组件
		skipComponents() {
			uni.navigateTo({
				url:'/pages/baseComponents/baseComponents'
			})
		},
		// 自定义组件
		skipCustomComponents() {
			uni.navigateTo({
				url:'/pages/customComponents/customComponents'
			})
		}
	}
}
</script>

<style>
	.box{
		display: flex;
		flex-direction: column;
	}
	button{
		height: 50px;
		margin-top: 10px;
	}
</style>
