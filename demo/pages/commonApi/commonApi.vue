<template>
	<view>
		<button type="default" @click="handleChangeTitle"> 改变标题 </button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		onLoad() {
			uni.showToast({
				title:'加载中',
				icon: 'loading'
			})
		},
		methods: {
			handleChangeTitle() {
				uni.setNavigationBarTitle({
					title: 'Api'
				})
			}
		}
	}
</script>

<style>

</style>
