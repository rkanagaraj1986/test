<template>
	<div class="row">
		<div
			class=""
			v-for="(quote, index) in quotes"
			:key="index"
			@click="delQuote(index)"
		>
			<appQuote>{{ quote }}</appQuote>
		</div>
	</div>
</template>

<script>
import Quote from "./Quote";
export default {
	name: "quotegrid",
	props: ["quotes"],
	components: { appQuote: Quote },
	data() {
		return {
			data: 0,
		};
	},
	methods: {
		delQuote(i) {
			this.$emit("delquote", i);
		},
	},
};
</script>

<style></style>
