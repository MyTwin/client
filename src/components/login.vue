<template>
    <div class="login-wrapper">
        <form action="">
            <div class="form-field">
                <label>Email</label>
                <input type="text" placeholder="Email" v-model="email">
            </div>
            <div class="form-field">
                <label>Password</label>
                <input type="password" placeholder="Password" v-model="password">
            </div>
            <input type="Submit" value="Login" @click.prevent="login">
        </form>
    </div>
</template>

<script>
import axios from 'axios'
import Swal from 'sweetalert2'

export default {
    data() {
        return {
            email: "",
            password: "",
            baseUrl: 'http://localhost:3000'
        }
    },
    methods: {
        login() {
            axios({
                method: 'post',
                url: `${this.baseUrl}/user/login`,
                data: {
                    email: this.email,
                    password: this.password
                }
            })
                .then(({data}) => {
                    this.email = ""
                    this.password = ""
                    localStorage.setItem('token', data.access_token)
                    Swal.fire({
                        icon: 'success',
                        title: 'Success',
                        text: 'Login success'
                    })
                    this.$emit('user-login', true)
                })
                .catch(err => {
                    Swal.fire({
                        icon: 'error',
                        title: 'Oops...',
                        text: `${err.response.data.message}`
                    })
                })
        }
    }
}
</script>

<style scoped>
    .login-wrapper {
        width: 80vw;
        height: calc(100vh - 3rem);
        margin: auto;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .login-wrapper form {
        width: 300px;
        padding: 3rem;
        border-radius: 4px;
        background-color: rgba(0, 0, 0, 0.2);
    }
    .form-field label {
        display: block;
        width: 100px;
        margin-bottom: 1rem;
    }
    .form-field input {
        width: 100%;
        height: 2rem;
        margin-bottom: 1rem;
        padding: 0 1rem;
    }
    input[type="submit"] {
        margin-top: 2rem;
        border: none;
        width: 100%;
        height: 2rem;
        margin-bottom: 1rem;
        cursor: pointer;
        background-color: #e04766;
        color: #fff;
        font-weight: bold;
    }
    input[type="submit"]:hover {
        background-color: #c51639;
        transition: 0.4s background-color;
    }
</style>