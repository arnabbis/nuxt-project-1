<template>
<div id="login">
    <h1>LOGIN:</h1>
    <form method="post" @submit="signUp">
        <input type="text" placeholder="User name" v-model="username" id="name"><br>

        <input type="password" placeholder="Password" v-model="password" id="password"><br>

        <button type="submit" @click="signUp">submit</button>
    </form>
</div>
</template>