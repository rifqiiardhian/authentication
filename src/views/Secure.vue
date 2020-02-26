<template>
    <div id="secure">
        <h1>SELAMAT DATANG !</h1>
        <p>
            Anda telah berhasil login
        </p>
        <router-link v-if="$store.state.isLoggedIn" to="/login" v-on:click.native="logout()" replace><button class="btn-logout">Logout</button></router-link>
    </div>
</template>

<script>
    export default {
        name: 'Secure',
    }
</script>

<style scoped>
    #secure {
        background-color: #FFFFFF;
        border: 1px solid #CCCCCC;
        padding: 50px;
        margin-top: 180px;
        border-radius: 10px;
        box-shadow: 0 15px 25px 0 rgba(0,0,0,0.2);
        border: 0px;
    }
    .btn-logout {
        background-color: #cfc20e;
        color: #fff;
        border: 0px;
        border-radius: 60px;
        margin: 5px 2px;
        padding: 10px 5px;
        cursor: pointer;
        transition: 0.3s;
        margin: 20px;
        width: 200px;
    }
    .btn-logout:hover {
        background-color: transparent;
        border: 2px solid #cfc20e;
        color: #cfc20e;
    }
</style>