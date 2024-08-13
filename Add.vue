<template>
    <Header />
    <h1>Hello User, Welcome on Add Restaurant page</h1>
    <form class="add">
        <input type="text" name="name" placeholder="Enter Name" v-model="restaurant.name"/>
        <input type="text" name="adresse" placeholder="Enter Adresse" v-model="restaurant.adresse"/>
        <input type="text" name="contact" placeholder="Enter Contact" v-model="restaurant.contact"/>
        <button type="button" v-on:click="addRestaurant">Add new Restaurant</button>
    </form>
</template>
<script>
    import Header from './Header.vue';
    import axios from 'axios';
    export default {
        name: 'AddPage',
        components: { Header },
        data(){
            return {
                restaurant: {
                    name:'',
                    adresse:'',
                    contact:''
                }
            }
        },
        methods: {
            async addRestaurant(){
                console.warn(this.restaurant)
                const result= await axios.post("http://localhost:3000/restaurants",{
                    name:this.restaurant.name,
                    adresse:this.restaurant.adresse,
                    contact:this.restaurant.contact,
                });
                if (result.status==201){
                    this.$router.push({name:'HomePage'});
                }
                console.warn("result ", result)
            }
        },
        mounted() {
            let user= localStorage.getItem("user-info");
            if (!user) {
                this.$router.push({name: 'SignUp'})
            }
        }
    }
</script> 