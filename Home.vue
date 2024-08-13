<template>
    <Header />
    <h1>Hello {{name}}, Welcome on Home page</h1>
    <table border="1">
        <tr>
            <td>ID</td>
            <td>Name</td>
            <td>Contact</td>
            <td>Adresse</td>
            <td>Actions</td>
        </tr>
        <tr v-for="item in restaurant" :key="item.id">
            <td>{{ item.id }}</td> 
            <td>{{ item.name }}</td> 
            <td>{{ item.contact }}</td> 
            <td>{{ item.adresse }}</td> 
            <td>
                <router-link class="custom-button" :to="'/update/'+item.id">Update</router-link>
                <button class="custom-button" v-on:click="deleteRestaurant(item.id)">Delete</button>
            </td> 
        </tr>
    </table> 
</template>
<script>
    import Header from './Header.vue';
    import axios from 'axios';
    export default {
        name: 'HomePage',
        data(){
            return{
                name:'',
                restaurant:[],
            }
        },
        components: { Header },
        methods: {
            async deleteRestaurant(id){
                let result= await axios.delete("http://localhost:3000/restaurants/" + id);
                console.warn(result)
                if(result.status==200){
                    this.loadData()
                }
            },
            async loadData(){
                let user= localStorage.getItem("user-info");
            this.name=JSON.parse(user).name;
            if (!user) {
                this.$router.push({name: 'SignUp'})
            }

            let result= await axios.get('http://localhost:3000/restaurants');
            console.warn(result)    
            this.restaurant=result.data;
            }
            
        },
        async mounted() {
            this.loadData();
        }
    }
</script> 
<style>
td{
    text-align: center;
    width: 160px;
    height: 40px;
}
</style>