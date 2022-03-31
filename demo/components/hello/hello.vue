<template>
	<text :style="{ color }"> hello </text>
</template>

<script>
export default {
	name:"hello",
	props:{
		color: {
			type: String,
			default: 'blue'
		}
	}
}
</script>

<style>

</style>
