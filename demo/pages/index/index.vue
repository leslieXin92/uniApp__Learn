<template>
	<view class="box">
		<button type="primary" @click="skipTemplateSyntax"> 模板语法 </button>
		<button type="primary" @click="skipDataBinding"> 数据绑定 </button>
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
		}
	}
};
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
