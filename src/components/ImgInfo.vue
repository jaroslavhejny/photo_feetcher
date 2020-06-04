<template>
 <div class="info">
  <h2
		class="author">
		{{ info.author}}
	</h2>

	<a
		:href="info['url']"
		target="_blank"
		class="link">
		{{ info.url }}
	</a>

 </div>
</template>

<script>
    export default {
        name: "ImgInfo",
        props: {
            info: Object
        }
    }
</script>

<style scoped>
 .info {
	width: 100%;
	background-color: rgba(0, 0, 0, 0.7);
	position: absolute;
	z-index: 2;
	color: aliceblue;
	bottom: 0rem;
 }

 .link {
	color: aliceblue;
	text-decoration: none;
	padding: 0 0.5rem 0 0.5rem;
 }

 .author {
	padding: 0 0.5rem 0 0.5rem;
 }
</style>