<template>
	<div class="results">
		<h1>{{ result }} Milliseconds</h1>
		<p>{{ rank }}</p>
	</div>
</template>

<script>
export default {
	data() {
		return {
			rank: null,
		};
	},
	props: ["result"],
	mounted() {
		this.rank = this.chooseRank(this.result);
	},
	methods: {
		chooseRank(result) {
			switch (true) {
				case result <= 250:
					return "Ninja reflexes";
				case result > 250 && result <= 450:
					return "Fast pace";
				default:
					return "Snail pace";
			}
		},
	},
};
</script>
<style></style>
