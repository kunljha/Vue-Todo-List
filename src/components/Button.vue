<template>
	<button
		class="btn"
		v-bind:style="{
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
