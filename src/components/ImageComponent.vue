<template>
	<div>

		<img
			:src="randomImgUrl"
			class="img">

		<img-info
			:info="imgInfo">
		</img-info>

		<loader :loading="loading"></loader>

	</div>



</template>

<script>
    import axios from "axios";

    import ImgInfo from "./ImgInfo";
    import Loader from "./Loader";

    export default {
        name: "ImageComponent",
        components: {
            Loader,
            ImgInfo
        },
        props: {
            position: Number,
            grayScale: Boolean,
            timestamp: Number
        },
        data() {
            return {
                size: 400,
                baseUrl: "https://picsum.photos",
                imgBaseUrl: "https://picsum.photos/id/",
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
                        this.loading = false;
                    })
                    .catch(e => {
                        console.error(e)
                    })
            }
        },

        mounted() {
            this.fetchImage();
        },

				watch: {
            timestamp() {
                this.fetchImage();
						}
				}
    }
</script>

<style scoped>
	.img {
		max-width: 100%;
		position: relative;
	}


</style>
