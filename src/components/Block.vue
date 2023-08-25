<template>
	<div class="area" v-if="showBlock">
		<div class="block" @click="stopTimer">
			<h1>Click me</h1>
		</div>
	</div>
</template>

<script>
export default {
	title: "Block",
	props: ["delay"],
	data() {
		return {
			showBlock: false,
			timer: null,
			reactionTime: 0,
		};
	},
	methods: {
		startTimer() {
			this.timer = setInterval(() => (this.reactionTime += 10), 10);
		},
		stopTimer() {
			clearInterval(this.timer);
			this.$emit("end", [this.reactionTime, this.showBlock]);
		},
	},
	mounted() {
		setTimeout(() => {
			this.showBlock = true;
			this.startTimer();
		}, this.delay);
	},
};
</script>

<style scoped>
.area {
	width: 100%;
	margin-top: 2rem;
	display: grid;
	place-content: center;
}

.block {
	display: flex;
	width: 300px;
	justify-content: center;
	align-items: center;
	padding: 4rem 6rem;
	background-color: greenyellow;
	cursor: pointer;
}
</style>
