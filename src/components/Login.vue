<template>
    <div>

 <form action ="javascript:void(0)">
        <h3>Email</h3>
        <input type="text" id="email-input">
        <h3>Password</h3>
        <input type = "password" id="password-input">
        <br>
        <input type = "submit" value = "Login" id="login-submit">
        </form>
        
<button @click="login" v-if="token == undefined">Login</button>

    </div>
</template>

<script>
    export default {
    name: "login-form",

    }
</script>

<style scoped>

</style>