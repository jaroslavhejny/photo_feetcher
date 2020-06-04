<template>
	<div v-if="!loading">

		<img
			:src="randomImgUrl"
			class="img">

		<img-info
			:info="imgInfo">
		</img-info>

	</div>
	<h1 v-else class="loader">LOADING</h1>


</template>

<script>
    import axios from "axios";

    import imgInfo from "./imgInfo";

    export default {
        name: "ImageComponent",
        components: {
            imgInfo
        },
        props: {
            position: Number,
            grayScale: Boolean,
        },
        data() {
            return {
                size: 400,
                baseUrl: "https://picsum.photos",
                imgBaseUrl: "https://i.picsum.photos/id/",
                id: undefined,
                loading: true,
                imgInfo: {}
            }
        },

        computed: {
            getRandom() {
                return `${this.baseUrl}/${this.size}`
            },

            grayscaleParam() {
                return this.grayScale ? '?grayscale' : ''
            },

            randomImgUrl() {
                return `${this.imgBaseUrl}${this.id}/${this.size}/${this.size}.jpg${this.grayscaleParam}`
            },

            imgInfoUrl() {
                return `${this.baseUrl}/id/${this.id}/info`
            }
        },

        methods: {
            fetchImage() {
                this.loading = true;
                axios.get(this.getRandom)
                    .then(response => {
                        this.id = response.headers["picsum-id"];
                        this.loading = false;
                        this.getImageInfo();
                    })
                    .catch(e => {
                        console.error(e)
                    })
            },

            getImageInfo() {
                axios.get(this.imgInfoUrl)
                    .then(response => {
                        this.imgInfo = response.data;
                    })
                    .catch(e => {
                        console.error(e)
                    })
            }
        },

        mounted() {
            this.fetchImage();
        }
    }
</script>

<style scoped>
	.img {
		max-width: 100%;
		width: 100%;
		height: auto;
		position: relative;
	}

	.loader {

	}
</style>
