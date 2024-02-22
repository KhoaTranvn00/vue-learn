<template>
	<hr />
	<h3>Assignment 6</h3>
	<input type="text" v-model="className" />
	<div :class="className">Style me!</div>
	<button @click="handleToggle">Toggle</button>
	<br />
	<input type="text" v-model="color" />
	<div :style="{ color }">style inline</div>
	<hr />
</template>

<script>
export default {
	data() {
		return {
			className: "",
			isToggle: false,
			color: "",
		};
	},

	methods: {
		handleToggle() {
			this.isToggle = !this.isToggle;
		},
	},
};
</script>

<style scoped>
.u1 {
	color: red;
}

.u2 {
	color: blue;
}
</style>
