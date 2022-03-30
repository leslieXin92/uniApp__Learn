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
