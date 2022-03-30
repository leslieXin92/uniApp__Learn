<template>
	<view>
		<view>{{ msg }}</view>
		<button type="default" @click="handleChangeMsg"> click </button>
	</view>
</template>

<script>
export default {
	data() {
		return {
			msg: 'hello world'
		}
	},
	methods: {
		handleChangeMsg() {
			const msg = this.msg==='hello world'? 'hola world':'hello world'
			this.msg = msg
		}
	}
}
</script>

<style>
</style>
