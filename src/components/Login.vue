<template>
    <section id="login">
        <input type="email" placeholder="Epost" v-model="credentials.email" v-bind:class="{  valid : validEmail }">
        <input type="password" placeholder="Password" v-model="credentials.password" v-bind:class="{  valid : validPassword }">
        <button>Login</button>
    </section>
</template>
<script>
export default {
    name: 'Login',
    data () {
        return {
            credentials: {
                email: '',
                password: ''
            }
        }
    },
    computed: {
        validEmail(){
            let re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
            return re.test(String(this.credentials.email).toLowerCase());
        },
        validPassword(){
            return (this.credentials.password.length >= 8) ? true : false
        }
    }
}
</script>
<style>
input:focus {
    outline: none;
    border: 1px solid red;
}

input.valid {
    border: 1px solid green;
}

</style>