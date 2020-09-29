<template>
    <div v-if="selection.name != undefined">
<h2> User Selection </h2>
<img :src="selection.image" alt="user selection image">

    </div>
</template>

<script>
    export default {
        name: "user-selection",

computed: {
    selection() {
        return this.$store.state.userSelection;
    }
},


    }
</script>

<style scoped>
#user {
 position: relative;
 right: 10%;
}
</style>