<template>

<div v-if="selection.name != undefined">
<h2> Computer Selection </h2>
<img :src="selection.image" alt="computer selection image">
</div>

</template>

<script>
    export default {
        name: "computer-selection",
      
    computed: {
    selection() {
        return this.$store.state.computerSelection;
    }
},
    }
</script>

<style scoped>

</style>