
<template>
    <form class="student-registartion container" method="get">
        <div class="row">
            <label class ="col-sm-3" >Name:</label>
            <input class ="col-sm-9" type="text" v-model="formvalues.name">
        </div>
        <div class="row">
            <label  class ="col-sm-3" for="gender">Gender:</label>
            <div class="col-sm-9 gender">
            <input type="radio" id="male" value="male" v-model="formvalues.gender">
            <label for="male">male</label><br>
            <input type="radio" id="female" value="female" v-model="formvalues.gender">
            <label for="female">female</label><br>
            </div>
        </div>
        <div class="row">
            <label class ="col-sm-3" >Email:</label>
            <input class ="col-sm-9" type="text" v-model="formvalues.email">
        </div>
        <div class="row">
            <label class ="col-sm-3" for="uname">Dob</label>
            <input class ="col-sm-9" type="text" v-model="formvalues.dob" >
        </div>
        <div class="row">
            <label class ="col-sm-3" for="pwd">Address:</label>
            <input class ="col-sm-9" type="password" v-model="formvalues.address">
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
         <button @click="register" >Submit</button>
    </form>
</template>
<style scoped lang="scss">   
 @import "studentRegistration.scss";
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
                    dob: '',
                    address: '',
                    gender:''
                }
            }
      },
     methods: {           
            register(){
               // e.preventDefault();
                let currentObj = this;
                let input={
                    name: this.formvalues.name,
                    gender: this.formvalues.gender,
                    email: this.formvalues.email,
                    dob: this.formvalues.dob,
                    address: this.formvalues.address,
                }
                console.log(input);
                axios.post('http://localhost:4000/students', input)
                .then(function (response) {
                    currentObj.output = response.data;
                    alert('added');
                })
                .catch(function (error) {
                    currentObj.output = error;
                });
            },

        }
  };
</script> 