<template>
<div>
    <h1>employes list</h1>
    <div>
        <table border="2px">
            <tr>
                <td>Id</td>
                <td>username</td>
                <td>Name</td>
                <td>Email</td>
                <td>Website</td>
                <td>Phone</td>
            </tr>
            <tr v-for="item in users" v-bind:key="item.id">
                <td>{{item.id}}</td>
                <td>{{item.name}}</td>
                <td>{{item.username}}</td>
                <td>{{item.email}}</td>
                <td>{{item.website}}</td>
                <td>{{item.phone}}</td>
                <td><button v-on:click="deleteUser(user.id)">Delete</button></td>
            </tr>
        </table>
    </div><br><br>
    <router-link to="/">Go To Home</router-link>
</div>
</template>

<script>
import Vue from 'vue';
import VueAxios from 'vue-axios';
import axios from 'axios';
Vue.use(VueAxios, axios)
export default {
    name: 'users',
    data() {
        return {
            users: null
        }
    },
    methods: {
        getUsers() {
            this.axios.get('https://jsonplaceholder.typicode.com/users').then((result)=>{
                console.warn(result)
                this.users=result.data
            })   
        },
        deleteuser(id)
        {
            this.axios.delete('https://jsonplaceholder.typicode.com/users/'+id).then((result)=>{
                console.warn(result)
                this.users=result.data
            })   
        }
    },
    mounted()
    {
        this.getUsers()
    }   
}
</script>
