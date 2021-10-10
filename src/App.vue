<template>
  <div id="app">
       <div class="container">
        <div class="row">

            <template v-if="!isUserLogged">
                <div class="col-md-4 offset-md-4">
                    <div class="login-form bg-light mt-4 p-4">
                        <form action="" method="" class="row g-3">
                            <h4>Welcome</h4>
                            <div class="col-12">
                                <label>Username</label>
                                <input type="text" name="username" class="form-control" placeholder="Email" v-model="user.email">
                            </div>
                            <div class="col-12">
                                <label>Password</label>
                                <input type="password" name="password" class="form-control" placeholder="Password" v-model="user.password">
                            </div>
                            <div class="col-12">
                                <button type="button" class="btn btn-dark float-end" @click="login">Login</button>
                            </div>
                        </form>
                        <hr class="mt-4">
                        <div class="col-12">
                            <p class="text-center mb-0">Have not account yet? <a href="#">Signup</a></p>
                        </div>
                    </div>
                </div>
            </template>
            <template v-else>
                    <h2>Bienvenido {{this.email}}</h2>

            </template>
        </div>
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
