<template>
    <div class="container">
        <form @submit.prevent="enviarFormulario">
            <h1>Novo Usuário</h1>
            <div class="form-group">
                <label for="nome">Nome</label>
                <input type="text" class="form-control" v-model="usuario.nome"/>
            </div>
            <div class="form-group">
                <label for="e-mail">E-mail</label>
                <input type="email" class="form-control" v-model="usuario.email" />
            </div>
            <div class="form-group">
                <label for="senha">Senha</label>
                <input type="password" class="form-control" v-model="usuario.senha" />
            </div>
            <button class="btn btn-primary" type="submit">Salvar</button>
        </form>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    data () {
        return {
            usuario: {
                nome: '',
                email: '',
                senha: ''
            }
        }
    },
    methods: {
        enviarFormulario () {
            axios.post('http://localhost:8000/auth/register', this.usuario)
                .then(() => this.$router.push({name: 'login'}) )
                .catch(e=> console.log(e))
        }
    }
}
</script>


