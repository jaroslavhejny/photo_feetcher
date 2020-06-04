<template>
	<div id="app">
		<h1 class="text-center">Photo fetcher</h1>
		<div class="header">
			<GrayScaleSwitch
				@grayScale="switchGrayScale"
				:grayScale="isGrayScale">
			</GrayScaleSwitch>

			<FetchButton
				class="float-right"
				@fetchNew="fetchNew">
			</FetchButton>
		</div>

		<div class="imgContainer">
			<div
				v-for="n in 4"
				:key="'imgContainer_' + n"
			>
				<ImageComponent
					:key="'img_' + n"
					:timestamp="timestamp"
					:position="n"
					:grayScale="isGrayScale"
					class="imageComponent"/>
			</div>
		</div>
	</div>
</template>

<script>
    import ImageComponent from "./components/ImageComponent";
    import GrayScaleSwitch from "./components/GrayScaleSwitch";
    import FetchButton from "./components/FetchButton";


    export default {
        name: "App",
        components: {
            ImageComponent,
            GrayScaleSwitch,
            FetchButton
        },
        data() {
            return {
                isGrayScale: false,
                timestamp: Date.now()
            }
        },
        methods: {
            fetchNew() {
                this.timestamp = Date.now();
            },

            switchGrayScale(isGrayScale) {
                this.isGrayScale = isGrayScale
            }
        }
    }
</script>

<style>
	#app {
		max-width: 750px;
		transform: translate(-50%, -50%);
		position: absolute;
		left: 50%;
		top: 50%;
	}

	.header {
		width: 100%;
		display: flex;
		justify-content: space-between;
		margin-bottom: 16px;
		align-items: center
	}

	.imgContainer {
		display: inline-grid;
		grid-template-columns: repeat(2, [col-start] 1fr);
		grid-gap: 16px;
	}

	.imageComponent {
		position: relative;
		bottom: 0;
	}
</style>
