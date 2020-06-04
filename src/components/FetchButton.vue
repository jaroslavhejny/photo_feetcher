<template>
 <button
   class="btn btn-primary"
   @click="handleClick">
  Fetch new photos
 </button>
</template>

<script>
    export default {
        name: "FetchButton",
        methods: {
            handleClick() {
                this.$emit("fetchNew")
            },
        }
    }
</script>

<style scoped>
 .button {
	display: block;
	background-color: #b48fec;
	color: aliceblue;
	border-radius: 0.25rem;
	border-color: #b48fec;
	padding: 10px;
	cursor: pointer;
 }
</style>