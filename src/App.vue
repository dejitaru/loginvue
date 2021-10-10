<template>
  <div id="app">

    <div class="container">
        <template v-if="!isUserLogged">
            <input type="email" v-model="user.email">
            <input type="password" v-model="user.password">
            <button type="button" @click="login">Login</button>
        </template>
        <template v-else>
            <h2>Bienvenido {{this.email}}</h2>

        </template>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'App',
  data() {
      return {
          isUserLogged: false,
          user: {},
          remoteUrl: "http://remoteurl.com"
      }
  },
  methods: {
      login() {
          if(this.user.email == "lucks17@gmail.com" && this.user.password == "123qwe") {
            axios.get(this.remoteUrl+ '?'+this.user.email).then((response)=>{
                console.log(response);
            })
          }
      }
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
