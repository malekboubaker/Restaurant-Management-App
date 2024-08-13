<template>
    <img class="logo" src="../assets/resto-logo-template-design-vector-33644681.jpg">
    <h1>Login</h1>
    <div class="login">
        <input type="text" v-model="email" placeholder="Enter your email"/>
        <input type="password" v-model="password" placeholder="Enter your password"/>
        <button v-on:click="login">Login</button>
        <p>
            <router-link to="/sign-up"> Sign Up </router-link>
        </p>
    </div>
</template>

<script>
    import axios from 'axios';
    export default {
        name:'LoginPage',
        data(){
            return {
                email:'',
                password:''
            }
        },
        methods:{
            async login(){
                let result = await axios.get(
                    `http://localhost:3000/user?email=${this.email}&password=${this.password}`
                )
                if (result.status==200 && result.data.length > 0){
                    localStorage.setItem("user-info",JSON.stringify(result.data [0]))
                    this.$router.push({name:'HomePage'})
                }
                console.warn(result)
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