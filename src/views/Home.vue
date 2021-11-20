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
            <tr v-for="item in list" v-bind:key="item.id">
                <td>{{item.id}}</td>
                <td>{{item.name}}</td>
                <td>{{item.username}}</td>
                <td>{{item.email}}</td>
                <td>{{item.website}}</td>
                <td>{{item.phone}}</td>
            </tr>
        </table>
    </div>
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
            list: null
        }
    },
    mounted() {
        Vue.axios.get('https://jsonplaceholder.typicode.com/users')
            .then(resp => {
                this.list = resp.data
                console.warn(resp.data)
            })
    }
}
</script>
