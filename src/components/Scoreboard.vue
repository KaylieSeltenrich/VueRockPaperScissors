<template>
  <div>
    <div id="scoreboard">
    <h2> Score : </h2>
    <h2> {{"Wins: " + wins}} </h2>
    <h2> {{"Draws: " + draws}}</h2>
    <h2> {{"Loses: " + loses}}</h2>
    </div>
  </div>
</template>

<script>
import cookies from "vue-cookies";

export default {
  name: "score-board",

  computed: {
    userSelection() {
      return this.$store.state.user;
    },

    computerSelection() {
      return this.$store.state.user;
    },

    wins(){
    return this.$store.state.wins;
  
    },
    
    loses(){
    return this.$store.state.loses;
    
    },
    
    draws(){
    return this.$store.state.draws;
  
    },

  },

};
</script>

<style scoped>
#scoreboard {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  border: 1px solid black;
  margin-left: 5%;
  margin-right: 5%;
}

</style>