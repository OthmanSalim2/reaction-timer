<template>
	<p>Reaction Time - {{ score }} ms</p>
	<p class="rank">{{ rank }}</p>
</template>

<script>
export default {
	props: ["score"],

	data() {
		return {
			rank: null,
		};
	},

	mounted() {
		if (this.score < 1000) {
			this.rank = "Hello World";
		} else if (this.score > 1000) {
			this.rank = "Snail Pace...";
		}
	},
};
</script>

<style>
.rank {
	font-size: 1rem;
	color: #1589ff;
	font-weight: bold;
}
</style>
