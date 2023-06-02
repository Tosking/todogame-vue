<template>
        <form @submit.prevent>
            <input type="text" v-model="login.email" class="input" placeholder="Email"/>
            <input type="text" v-model="login.password" class="input" placeholder="Password"/>
            <button class="button" @click="loginUser">
                Login
            </button>
        </form>
</template>

<script>
import axios from "axios";
export default {
    data(){
        return{
            login: {
                email: '',
                password: ''
            }
        }
    },
    methods: {
        isEmptyOrSpaces(str){
            return str === null || str.match(/^ *$/) !== null;
        },
        loginUser(){
            if(this.isEmptyOrSpaces(this.login.email) || this.isEmptyOrSpaces(this.login.password)){
                return;
            }
            axios.post("http://127.0.0.1:5000/login", this.login)
            .then(response => {this.$emit('login', response.data.id[0]); console.log(response)}).catch(error => console.log(error));
            this.login = {
                email: '',
                password: ''
            }
        }
        
    }
}
</script>

<style>

</style>