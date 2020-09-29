<template>
  <div>
    <form action="javascript:void(0)">
    <p v-if="token == undefined">Email</p>
    <input type="text" id="" v-model="email" v-if="token == undefined" />
    <p v-if="token == undefined">Password</p>
    <input type="password" id="" v-model="password" v-if="token == undefined" />
    </form>
    <h3 @click="login" v-if="token == undefined"> Login </h3>
    <h3 @click="goToGame" v-else>You are already logged in! Click here to go to game.</h3>
    <h4>{{ status }}</h4>
  </div>
</template>

<script>

import axios from "axios";
import cookies from "vue-cookies";

export default {
  name: "login-form",

  data() {
    return {
      email: "",
      password: "",
      status: "",
      token: cookies.get("loginToken"),
    };
  },

  methods: {
    login: function() {
      axios
        .request({
          url: "https://reqres.in/api/login",
          method: "POST",
          headers: {
            "Content-Type": "application/json"
          },
          data: {
            email: this.email,
            password: this.password
          }
        })
        .then(response => {
        
           cookies.set("loginToken", response.data.token);
           this.$router.push("/game");
      
        })
        .catch(error => {
          console.log(error);
          this.status = "Login Error!";
        });
    },

    goToGame: function(){
    this.$router.push("/game");
    }
  }
};
</script>

<style scoped>
</style>