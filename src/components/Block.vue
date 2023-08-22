<template>
	<div class="block" v-if="showBlock" @click="stopTimer">click me</div>
</template>

<script>
export default {
	props: ["delay"],
	data() {
		return {
			showBlock: false,
			timer: null,
			reactionTime: 0,
		};
	},

	// the commands inside mounted method will executed automatically when execute the specific action
	mounted() {
		console.log("component mounted");
		this.startTimer();
		setTimeout(() => {
			this.showBlock = true;
			console.log(this.delay);
		}, this.delay);
	},

	methods: {
		startTimer() {
			this.timer = setInterval(() => {
				this.reactionTime += 10;
			}, 10);
		},

		stopTimer() {
			clearInterval(this.timer);
			this.$emit("end", this.reactionTime);
		},
	},

	// this method it executed after mounted method
	// updated() {
	// 	console.log("component updated");
	// },

	// this method executed if happened any error in called router, like deleted the calling Block component
	// unmounted() {
	// 	console.log("unmounted component");
	// },
};
</script>

<style>
.block {
	width: 400px;
	border-radius: 20px;
	background: #0faf87;
	color: white;
	text-align: center;
	padding: 100px 0;
	margin: 40px auto;
}
</style>
