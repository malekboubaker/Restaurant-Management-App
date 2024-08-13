<template>
    <img class="logo" src="../assets/resto-logo-template-design-vector-33644681.jpg">
    <h1>Sign Up</h1>
    <div class="register">
        <input type="text" v-model="name" placeholder="Enter your name"/>
        <input type="text" v-model="email" placeholder="Enter your email"/>
        <input type="password" v-model="password" placeholder="Enter your password"/>
        <button v-on:click="signUp" >Sign Up</button>
        <p>
            <router-link to="/login"> Login </router-link>
        </p>
    </div>
</template>

<script>
import axios from 'axios';
export default {
    name: "SignUp",
    data() {
        return {
            name: "",
            email: "",
            password: ""
        }
    },
    methods :{
        async signUp() {
            let result = await axios.post("http://localhost:3000/user",{
                email: this.email,
                password: this.password,
                name: this.name
            });

            console.warn(result);
            if (result.status==201){
                localStorage.setItem("user-info",JSON.stringify(result.data))
                this.$router.push({name:'HomePage'})
            }
        }
    },
    mounted() {
        let user= localStorage.getItem("user-info");
        if (user) {
            this.$router.push({name: 'HomePage'})
        }
    }
}
</script>

<style>

</style>