<template>
    <div id="login">
        <h1 class="title">Login</h1>
        <form class="">
        <div class="form-group">
            <input type="text" class="form-control" name="username" v-model="input.username" placeholder="Username" />
        </div>
        <div class="form-group">
             <input type="password" class="form-control" name="password" v-model="input.password" placeholder="Password" />
        </div>
        <button type="button" class="btn btn-login" v-on:click="login()">LOGIN</button>
        </form>
    </div>
</template>

<script>
    export default {
        name: 'Login',
        data() {
            return {
                input: {
                    username: "",
                    password: ""
                }
            }
        },
        methods: {
            login() {
                // eslint-disable-next-line no-cond-assign
                if(this.input.username != "" && this.input.password != "") {
                    if(this.input.username == this.$parent.mockAccount.username && this.input.password == this.$parent.mockAccount.password) {
                        this.$emit("authenticated", true);
                        this.$router.replace({ name: "Secure" });
                    } else {
                        console.log("The username and / or password is incorrect");
                    }
                } else {
                    console.log("A username and password must be present");
                }
            }
        }
    }
</script>

<style scoped>
    .title {
        padding-bottom: 20px;
    }
    #login {
        width: 400px;
        border: 1px solid #CCCCCC;
        background-color: #FFFFFF;
        margin: auto;
        margin-top: 130px;
        padding: 50px;
        border-radius: 10px;
        box-shadow: 0 15px 25px 0 rgba(0,0,0,0.2);
        border: 0px;
    }
    .btn-login {
        background-color: #cfc20e;
        color: #fff;
        border: 0px;
        border-radius: 60px;
        margin: 5px 2px;
        padding: 10px 5px;
        cursor: pointer;
        transition: 0.3s;
        margin: 20px;
        width: 150px;
    }
    .btn-login:hover {
        background-color: transparent;
        border: 2px solid #cfc20e;
        color: #cfc20e;
    }
    input[type=text] {
        height: 50px;
        border-radius: 50px;
        padding-left: 20px;
    }
    input[type=password] {
        height: 50px;
        border-radius: 50px;
        padding-left: 20px;
    }
</style>