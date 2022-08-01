<template>
<div>
    <h1>LOGIN:</h1>
    <form method="post">
        <input type="text" placeholder="User name" v-model="username" id="name" name="uname" required><br>

        <input type="password" placeholder="Password" v-model="password" id="password" name="psw" required><br>

        <button type="submit" @click="signUp">submit</button>
    </form>
</div>
</template>

<script>
export default {
    data(){
        return{
            username:'',
            password:'',
        }
    },
    methods:{
        signUp(){

        }
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
