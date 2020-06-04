<template>
	<div
		v-if="loading"
		class="loader">
		<h1>LOADING</h1>
	</div>
</template>

<script>
    export default {
        name: "Loader",
				props: {
            loading: Boolean
				}
    }
</script>

<style scoped>
	.loader {
		background-color: rgba(180, 143, 236, 0.78);
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		z-index: 1000;
	}

	h1 {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
	}
</style>