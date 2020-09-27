<template>
  <div>
    <p>Email</p>
    <input type="text" id="" v-model="email" />
    <p>Password</p>
    <input type="password" id="" v-model="password" />
    
    <h3 @click="login" v-if="token == undefined"> Login </h3>
    
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
          console.log(response);
           cookies.set("loginToken", response.data.token);
           this.$router.push("/game")
        })
        .catch(error => {
          console.log(error);
          this.status = "Login Error!";
        });
    }
  }
};
</script>

<style scoped>
</style>