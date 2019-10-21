<template>
    <div class="col-lg-4 offset-lg-4">
        <form @submit.prevent="register">
            <div class="form-group">
                <label for="name">Name</label>
                <input id="name" class="form-control" type="text" v-model="name" required autofocus>
            </div>
            <div class="form-group">
                <label for="email" >E-Mail Address</label>
                <input id="email" class="form-control" type="email" v-model="email" required>
            </div>
            <div class="form-group">
                <label for="password">Password</label>
                <input id="password" class="form-control" type="password" v-model="password" required>
            </div>
            <div class="form-group">
                <label for="password-confirm">Confirm Password</label>
                <input id="password-confirm" class="form-control" type="password" v-model="password_confirmation" required>
            </div>
            <p>Already have an account? <router-link to="/login"> Register </router-link></p>
            <div>
                <button type="submit" class="btn btn-primary">Register</button>
            </div>
        </form>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                name: '',
                email: '',
                password: '',
                password_confirmation: ''
            }
        },
        methods: {
            register() {
                let data = {
                    name: this.name,
                    email: this.email,
                    password: this.password
                }
                this.$store.dispatch('register', data).then(() => {
                    this.$router.push('/');
                }).catch(err => {
                    console.log(err);
                })
            }
        },
    }
</script>

<style lang="scss" scoped>

</style>