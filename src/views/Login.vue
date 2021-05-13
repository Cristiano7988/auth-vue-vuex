<template>
    <div class="container">
        <form @submit.prevent="efetuarLogin">
            <h1>Login</h1>
            <div class="form-group">
                <label for="e-mail">E-mail</label>
                <input type="email" class="form-control" v-model="usuario.email" />
            </div>
            <div class="form-group">
                <label for="senha">Senha</label>
                <input type="password" class="form-control" v-model="usuario.senha" />
            </div>
            <button class="btn btn-primary btn-block" type="submit">
                Logar
            </button>
            <router-link :to="{ name: 'novo.usuario' }">
                Cadastre-se aqui!
            </router-link>
        </form>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    data () {
        return {
            usuario: {}
        }
    },
    methods: {
        efetuarLogin () {
            axios.post('http://localhost:8000/auth/login', this.usuario)
                .then(r => {
                    localStorage.setItem('token', r.data.access_token)
                    this.$router.push({name: 'gerentes'})
                })
                .catch(e => console.log(e))
        }
    }
}
</script>


