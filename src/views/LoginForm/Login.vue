<template>
  <form class="user-login">
    <div class="row">
      <label class="col-sm-3">User Name:</label>
      <input class="col-sm-9" type="text" v-model="form.uname" >
    </div>
    <div class="row">
      <label class="col-sm-3">Password:</label>
      <input class="col-sm-9" type="password" v-model="form.pwd" >
    </div>
     <button class="login-btn" @click="login" >Login</button>
    </form>
</template>
<script>
import axios from "axios";
//import router from "./src/router/index.js";
//import router from '../router';
//Vue.loadScript("login.js")
import Router from '../../router/index.js';
export default {
  name: "Home",
  components: {
    // HelloWorld,
  },
  data() {
    return {
      form: {
        uname: '',
        pwd: ''
      }
    };
  },
  methods:{
    login(){
        let currentObj = this;
        let input={
            uname: this.form.uname,
            pwd: this.form.pwd
        }
        console.log(input);
        axios.post('http://localhost:4000/login', input)
        .then(function (response) {
          //Set header to session storage
          //redirect user to student list
            sessionStorage.setItem('token', response.data.token);
            currentObj.output = response.data;
            console.log(response.data.token);
            if(response.data.token != null ){
                console.log("Logged in");               
                Router.push('/studentdetails'); 
            }
            else{
              alert('invalid');
            }         
        })
        .catch(function (error) {
            currentObj.output = error;
              console.log("error")  
        });
    },
  }
};
</script>
<style scoped lang="scss">
@import "login.scss";
</style>
