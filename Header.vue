<template>
    <div class="nav">
        <router-link to="/">Home</router-link>
        <router-link to="/add">Add Restaurant</router-link> 
        <a v-on:click="logout" href="#">logout</a>
    </div>
</template>
<script>
  export default {
        name: 'HeaderPage',
        methods:{
            logout(){
                localStorage.clear();
                this.$router.push({name:'LoginPage'})
            }
        }
    }
</script>
<style>

.nav {
    background-color: #333;
    overflow: hidden;
}

.nav a {
    float: left;
    margin-right: 5px;
    color: #f2f2f2f2;
    text-align: center;
    padding: 14px 16px;
    text-decoration: none;
    font-size: 17px;
}

.nav a:hover {
    background-color: #ddd;
    color: black;
}
</style>