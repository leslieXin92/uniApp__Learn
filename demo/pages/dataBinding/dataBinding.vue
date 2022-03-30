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
