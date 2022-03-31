<template>
	<text :style="{ color }"> world </text>
</template>

<script>
export default {
	name:"world",
	props: {
		color: {
			type: String,
			default: 'blue'
		}
	}
}
</script>

<style>

</style>
