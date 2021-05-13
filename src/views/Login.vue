<template>
    <div class="container">
        <form @submit.prevent="enviarFormulario">
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
export default {
    data () {
        return {
            usuario: {}
        }
    }
}
</script>


