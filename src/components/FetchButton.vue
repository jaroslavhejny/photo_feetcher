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