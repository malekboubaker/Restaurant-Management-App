<template>
    <Header />
    <h1>Hello User, Welcome on Update Restaurant page</h1>
    <form class="add">
        <input type="text" name="name" placeholder="Enter Name" v-model="restaurant.name"/>
        <input type="text" name="adresse" placeholder="Enter Adresse" v-model="restaurant.adresse"/>
        <input type="text" name="contact" placeholder="Enter Contact" v-model="restaurant.contact"/>
        <button type="button" v-on:click="updateRestaurant">Update Restaurant</button>
    </form>
</template>
<script>
    import Header from './Header.vue';
    import axios from 'axios';
    export default {
        name: 'UpdatePage',
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
            async updateRestaurant(){
                console.warn(this.restaurant)
                const result= await axios.put("http://localhost:3000/restaurants/"+this.$route.params.id,{
                    name:this.restaurant.name,
                    adresse:this.restaurant.adresse,
                    contact:this.restaurant.contact,
                });
                if (result.status==200){
                    this.$router.push({name:'HomePage'});
                }                
            }  
        },
        async mounted() {
            let user = localStorage.getItem("user-info");
            if (!user) {
                this.$router.push({ name: 'SignUp' });
            }

            const result = await axios.get('http://localhost:3000/restaurants/'+this.$route.params.id)
            //console.warn(this.$route.params.id)
            console.warn(result.data)
            this.restaurant=result.data
        }

    }
</script> 