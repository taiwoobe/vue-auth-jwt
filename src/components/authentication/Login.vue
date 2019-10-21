<template>
    <div class="col-lg-4 offset-lg-4">
        <form class="login" @submit.prevent="login">
            <h1>Sign in</h1>
            <div class="form-group">    
                <label>Email</label>
                <input class="form-control" required v-model="email" type="email" placeholder="Email Address"/>
            </div>
            <div class="form-group">
                <label>Password</label>
                <input class="form-control" required v-model="password" type="password" placeholder="Password"/>
            </div>
           <button type="submit" class="btn btn-primary">Login</button>
        </form>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                email: '',
                password: ''
            }
        },
        methods: {
            login() {
                const { email, password } = this;
                this.$store.dispatch("login", {email, password}).then(() => {
                    this.$router.push('/');
                })
                .catch(err => {
                    console.log(err);
                })
            }
        },
    }
</script>

<style lang="scss" scoped>

</style>