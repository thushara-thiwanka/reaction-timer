<template>
	<main>
		<h1>Reaction Timer</h1>
		<h4>Click the block soon as it appears to find the reaction time.</h4>
		<button @click="start">Start</button>
		<Block v-if="isPlaying" :delay="delay" @end="end" />
		<Result v-if="result !== 0" :result="result" />
	</main>
</template>

<script>
import "./assets/global.css";
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";

export default {
	name: "App",
	components: {
		Block,
		Result,
	},
	data() {
		return {
			delay: 2000,
			isPlaying: false,
			result: 0,
		};
	},
	methods: {
		start() {
			this.delay += Math.random() * 5000;
			this.isPlaying = true;
			this.result = 0;
		},
		end([reactionTime]) {
			this.isPlaying = false;
			this.result = reactionTime;
		},
	},
};
</script>

<style>
#app {
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}

main {
	height: 100vh;
	text-align: center;
}

button {
	outline: none;
	padding: 0.8rem 1.8rem;
	border: none;
	border-radius: 5px;
	background-color: rgb(68, 227, 40);
	color: white;
	font-size: 1rem;
	font-weight: bold;
	cursor: pointer;
}
</style>
