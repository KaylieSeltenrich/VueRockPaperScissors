<template>
<div>
  <div v-if="token!=undefined">
    
    <score-board> </score-board>
    <h2>Choose one:</h2>
    <div id="choices">
      <button id="rock" @click="select(0)">Rock</button>
      <button id="paper" @click="select(1)">Paper</button>
      <button id="scissors" @click="select(2)">Scissors</button>
    </div>
    <div id="game-play">
    <user-selection> </user-selection> 
    <computer-selection> </computer-selection>
    </div>
    <br />
    <h3 @click="deleteCookies">Click here to Logout</h3>
   
  </div>
  <h3 v-else> Error! You need to be logged in to view the game.
    <br>
    <button @click="$router.push('/')"> Click here to return to the Login Page! </button> </h3>
</div>
</template>

<script>
import UserSelection from "../components/Userselection.vue";
import ScoreBoard from "../components/Scoreboard.vue";
import ComputerSelection from "../components/Computerselection.vue";
import cookies from "vue-cookies";

    export default {
      name: "game-page",
       components: {
           UserSelection,
           ScoreBoard,
           ComputerSelection,
       },
       
    data: function() {
        return {
            gamechoices: [
                {
                    name: "Rock",
                    image: "https://icon-library.com/images/rock-paper-scissors-icon/rock-paper-scissors-icon-24.jpg"
                },
                {
                    name: "Paper",
                    image: "https://static.thenounproject.com/png/477922-200.png"
                },
                {
                    name: "Scissors",
                    image: "https://static.thenounproject.com/png/88666-200.png"
                },
                

            ],

          token :
            cookies.get("loginToken"),
          
    
     gamerules: {
            Rock: {
            Rock: 0,
            Paper: -1,
            Scissors: 1
            },
            Paper: {
            Rock: 1,
            Paper: 0,
            Scissors: -1,
            },
            Scissors: {
              Rock: -1,
              Paper: 1,
              Scissors: 0
            }
            },
    }
    
    },

    methods: {
        select: function(index) {
            let userSelection = this.gamechoices[index];
            let computerSelection = this.gamechoices[Math.floor(Math.random()*3)];
            let result = this.gamerules[userSelection.name][computerSelection.name];
            this.$store.commit("updateUser", userSelection);
            this.$store.commit("updateComputer", computerSelection);
            this.$store.commit("updateResults",result);
            
        },

        deleteCookies: function(){
          cookies.remove("loginToken"),
          this.$router.push("/")
        },
    },
    }
</script>

<style scoped>
#game-play {
  display: grid;
  grid-template-columns: 1fr 1fr;
}
</style>