<template>
  <div class="login-page">
    <router-link to="/demo">
      <button class="btn">Demo</button>
    </router-link>
    <div class="form">
      <input type="email" placeholder="Usuario" v-model="email"/>
      <input type="password" placeholder="Clave" v-model="password"/>
      <button @click="logIn()"><span v-if="fetchingUser">Iniciando sesion...</span><span v-else>Iniciar sesión</span></button>
      <span class="error" v-if="error">{{ error }}</span>
      <p class="message">¿No registrado? <router-link class="link" to="/register">Crear cuenta</router-link></p>
      <p class="message"><router-link class="link" to="/forgotPass">He olvidado mi clave</router-link></p>
    </div>
  </div>
</template>

<script>
import { mapActions, mapGetters, mapState } from 'vuex'

export default {
  data () {
    return {
      email: 'juanjo_810@usal.es',
      password: 'asdqwe'
    }
  },
  computed: {
    ...mapState([
      'fetchingUser',
      'error'
    ]),
    ...mapGetters([
      'getUser'
    ]),
    user () {
      return this.getUser
    }
  },
  methods: {
    ...mapActions([
      'loginUser',
      'getCurrentUser'
    ]),
    async logIn () {
      if (this.email !== '' || this.password !== '') {
        await this.loginUser({ email: this.email, password: this.password })
        this.email = ''
        this.password = ''
        if (this.error === '') {
          this.$router.push({name: 'dashboard'})
        }
      }
    }
  }
}
</script>

<style scoped>
  .login-page {
    width: 25%;
    padding: 8% 0 0;
    margin: auto;
  }
  .form {
    z-index: 1;
    background: #FFFFFF;
    padding: 10%;
    text-align: center;
    box-shadow: 0 0 20px 0 rgba(0, 0, 0, 0.2), 0 5px 5px 0 rgba(0, 0, 0, 0.24);
  }
  .form input {
    font-family: "Roboto", sans-serif;
    outline: 0;
    background: #f2f2f2;
    width: 100%;
    border: 0;
    margin: 0 0 15px;
    padding: 15px;
    box-sizing: border-box;
    font-size: 14px;
  }
  .btn{
    font-family: "Roboto", sans-serif;
    text-transform: uppercase;
    outline: 0;
    background: #28d;
    width: 40%;
    border: 0;
    padding: 15px;
    margin-left: 120%;
    color: #FFFFFF;
    font-size: 14px;
    -webkit-transition: all 0.3 ease;
    transition: all 0.3 ease;
    cursor: pointer;
  }
  .btn:hover,.btn:active,.btn:focus {
    background: #17c;
  }
  .form button {
    font-family: "Roboto", sans-serif;
    text-transform: uppercase;
    outline: 0;
    background: #28d;
    width: 100%;
    border: 0;
    padding: 15px;
    color: #FFFFFF;
    font-size: 14px;
    -webkit-transition: all 0.3 ease;
    transition: all 0.3 ease;
    cursor: pointer;
  }
  .form .message {
    margin: 15px 0 0;
    color: #b3b3b3;
    font-size: 12px;
  }
  .form .message .link{
    color: #17c;
    text-decoration: none;
  }
  .error{
    color: red;
  }
</style>
