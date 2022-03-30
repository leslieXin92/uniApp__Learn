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