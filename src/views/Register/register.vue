
<template class="container">
    <form class="user-registartion" method="get">
        <div class="row">
            <label class ="col-sm-3" >Name:</label>
            <input class ="col-sm-9" type="text" v-model="formvalues.name">
        </div>
        <!--<div class="row">
            <label  class ="col-sm-3" for="gender">Gender:</label>
            <div class="col-sm-9 gender">
            <input type="radio" id="male" value="male" v-model="formvalues.gender">
            <label for="male">male</label><br>
            <input type="radio" id="female" value="female" v-model="formvalues.gender">
            <label for="female">female</label><br>
            </div>
        </div>-->
        <div class="row">
            <label class ="col-sm-3" >Email:</label>
            <input class ="col-sm-9" type="text" v-model="formvalues.email">
        </div>
        <div class="row">
            <label class ="col-sm-3" for="uname">User Name:</label>
            <input class ="col-sm-9" type="text" v-model="formvalues.uname" >
        </div>
        <div class="row">
            <label class ="col-sm-3" for="pwd">Password:</label>
            <input class ="col-sm-9" type="password" v-model="formvalues.pwd">
        </div>
        <!--<div class="row">
            <label class ="col-sm-3" for="pwd">Role:</label>
            <select class ="col-sm-9" type="text" v-model="formvalues.role">
                <option>Web Designer</option>
                <option>Web Developer</option>
            </select>
        </div>
        <div class="row">
            <label class ="col-sm-3" for="pwd">Skills:</label>
            <input class ="col-sm-9" type="text" v-model="formvalues.txtSkills" @keyup="addSkills"> 
            <div v-for="skill in formvalues.skills" :key = "skill">
                <span>{{skill}}</span>
            </div>
        </div>-->
         <button class="user-register-btn" @click="register" >Submit</button>
    </form>
</template>
<style scoped lang="scss">   
 @import "register.scss";
</style>
<script>
//Vue.loadScript("login.js")
import axios from "axios";
  export default {
      name: "Home",
      data(){
          return{
              formvalues:{
                    name: '',
                    email:'',
                    uname: '',
                    pwd: ''
                }
            }
      },
     methods: {           
            register(){
               // e.preventDefault();
                let currentObj = this;
                let input={
                    name: this.formvalues.name,
                    email: this.formvalues.email,
                    uname: this.formvalues.uname,
                    pwd: this.formvalues.pwd,
                }
                console.log(input);
                axios.post('http://localhost:4000/user', input)
                .then(function (response) {
                    currentObj.output = response.data;
                })
                .catch(function (error) {
                    currentObj.output = error;
                });
            },
            getData(){
                axios.get('http://localhost:4000/students')
                .then(function (response) {
                    // handle success
                    console.log(response);
                })
                .catch(function (error) {
                    // handle error
                    console.log(error);
                })
                .then(function () {
                    // always executed
                });
            }
        }
  };
</script> 