<template>
	<div class="panel-body" v-local-bg:delayed.blink="'green'">
		<div class="quote">
			<slot></slot>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			quote: "A Wonderful Quote",
		};
	},
	directives: {
		"local-bg": {
			bind(el, binding) {
				if (binding.arg === "delayed") {
					if (binding.modifiers["blink"]) {
						setTimeout(() => {
							let pri = "red";
							let sec = binding.value;
							let curcolor = pri;
							setInterval(() => {
								curcolor === pri ? (curcolor = sec) : (curcolor = pri);
								el.style.backgroundColor = curcolor;
							}, 500);
						}, 2000);
					}
				} else {
					el.style.backgroundColor = binding.value;
				}
			},
		},
	},
};
</script>

<style scoped>
.panel-body {
	font-size: 24px;
}
.quote {
	cursor: pointer;
}
.quote-hover {
	background-color: #ffe2e2;
}
</style>
