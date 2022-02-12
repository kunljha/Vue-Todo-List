<template>
	<button
		class="btn"
		:style="{
			backgroundColor: color,
		}"
	>
		{{ text }}
	</button>
</template>

<script>
export default {
	name: 'Button',
	props: {
		text: String,
		color: String,
	},
}
</script>
