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

<script>
	export default {
		data() {
			return {}
		}
	}
</script>

<style>
	.box{
		margin-left: 10px;
	}
	scroll-view{
		width: 200px;
		height: 100px;
		margin: 10px auto;
		outline: 2px solid #4CD964;
	}
	scroll-view view{
		width: 120%;
		margin-top: 10px;
		background-color: #007AFF;
	}
	swiper{
		width: 300px;
		margin: 10px auto;
		outline: 2px solid #007AFF;
	}
	swiper-item{
		line-height: 130px;
		font-size: 26px;
		text-align: center;
		background-color: #4CD964;
	}
</style>
