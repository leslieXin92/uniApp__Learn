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
