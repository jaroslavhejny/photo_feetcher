<template>
	<div class="custom-control custom-switch">
		<input
			v-model="isGrayScale"
			@change="handleChange"
			type="checkbox"
			class="custom-control-input"
			id="grayScaleSwitch">

		<label
			class="custom-control-label"
			for="grayScaleSwitch">
			Make photos grayscale
		</label>
	</div>
</template>

<script>
    export default {
        name: "GrayScaleSwitch",
        props: {
            grayScale: Boolean
        },
        data() {
            return {
                isGrayScale: this.grayScale
            }
        },
        methods: {
            handleChange() {
                this.$emit("grayScale", this.isGrayScale)
            }
        }
    }
</script>

<style scoped>

</style>