<template>
    <div>
        <h1>List of Users</h1>
        <table border="1px">
            <tr>
                <td>Name</td>
                <td>Username</td>
                <td>Password</td>
            </tr>
            <tr v-for="item in list" v-bind:key="item.id" >
                <td>{{item.fullName}}</td>
                <td>{{item.username}}</td>
                <td>{{item.password}}</td>
            </tr>
        </table>
    </div>
</template>
<script>
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'
Vue.use(VueAxios, axios)
export default {
    name: 'ListUsers',
    data() {
        return {
            list:undefined
        }
    },
    mounted() {
        Vue.axios.get('https://6145859338339400175fc5f1.mockapi.io/api/admin')
        .then((resp) =>{
            this.list = resp.data;
            console.warn(resp.data)
        })
    }    
}
</script>
<style scoped>

</style>