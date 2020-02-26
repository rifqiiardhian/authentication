<template>
  <div id="app" class="container">
    <div id="nav" class="nav nav">  
      
    </div>
    <router-view @authenticated="setAuthenticated" />
  </div>
</template>
<script>
    export default {
        name: 'App',
        data() {
            return {
                authenticated: false,
                mockAccount: {
                    username: "admin",
                    password: "admin"
                }
            }
        },
        mounted() {
           if (localStorage.getItem('isLoggedIn')){ 
             this.$store.state.isLoggedIn = JSON.parse(localStorage.getItem('isLoggedIn'))
           }
           if(!this.$store.state.isLoggedIn) {              
             this.$router.replace({ name: "Login" }).catch(err=>err);
            }
        },
        methods: {
            setAuthenticated(status) {
                this.$store.commit('setLogin',status)
                localStorage.setItem('isLoggedIn', JSON.stringify(this.$store.state.isLoggedIn));
            },
            logout() {
                localStorage.removeItem('isLoggedIn');
                this.$store.commit('revokeLogin')
            }
        }
    }
</script>

<style>
    h1 {
        padding: 0;
        margin-top: 0;
    }
    #app {
       font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
        margin: auto;
    }
</style>