<template>
<div>
    <h1>Login:</h1>
    <form method="post">
        <input type="text" placeholder="User name" v-model="username" id="name"><br>

        <input type="password" placeholder="Password" v-model="password" id="password"><br>

        <button type="submit" @click="login"><NuxtLink to="bucket">submit</NuxtLink></button>
    </form>
</div>
</template>
<script>
import axios from "axios"
export default{
    name:"login",
    data(){
        return{
            username:"",
            password:""
        }
    },
    methods:{
        async login(){
            let result=await axios.get(
                `http://localhost:3000/users?username=${this.username}&password=${this.password}`
            );
            if(result.status==200 && result.data.length>0){
                this.$router.push({name:"bucket"})
            }
            else{
                alert("please enter correct username and password")
            }
            //console.log(result)
            }
            // console.log(this.email,this.password)
    }
}
</script>
<style scoped>
div {
    text-align: center;
    width: 100%;
    margin: 0 auto;
    padding: 0px;
    background-color: grey;
    /* margin: 20; */
    /* padding: 45pc; */
}

input[type=text],
input[type=password] {
    background-color: rgb(197, 193, 193);
    width: 20%;
    padding: 12px 20px;
    border-radius: 4px;
    margin: 8px 2px;
    display: inline-block;
    border: 1px solid rgb(17, 17, 17);
    box-sizing: border-box;
}

button {
    background-color: #afb4b2;
    color: white;
    padding: 14px;
    margin: 2px;
    border: 1px solid rgb(17, 17, 17);
    cursor: pointer;
    width: 20%;

}
</style>