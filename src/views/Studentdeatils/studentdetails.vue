<template>
  <div class="student-details container">
    <h1>Students Details</h1>
    <!--<button @click=getData()>Get Data</button>-->
    <div class="btn-wrapper pull-right">
      <button @click='addStudent'>Add</button>
    </div>
    <table>
      <thead>
        <tr>
          <th class="text-left"></th>
          <th class="text-left">Name</th>
          <th class="text-left">DOB</th>
           <th class="text-left">Gender</th>
          <th class="text-left">Address</th>
          <th class="text-left">Email</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="stud in studentData.studDetails" :key="stud._id">
          <td><input type="checkbox"></td>
          <td>{{ stud._id }}</td>
          <td>{{ stud.name }}</td>
          <td>{{ stud.dob }}</td>
          <td>{{ stud.gender }}</td>
          <td>{{ stud.address }}</td>
          <td>{{ stud.email }}</td>
          <td><button @click="updateStudentDetails()">Update</button></td>
          <td><button @click="deleteStudent(stud, stud._id)">Delete</button></td>
        </tr>
      </tbody>
  </table>
  </div>
</template>
<style scoped lang="scss">   
 @import "studentdetails.scss";
</style>
<script>
import axios from "axios";
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
      },
      studentData: {
        status: '',
        studDetails: []
      },
      
    };
  },
  mounted:function(){
        this.getData() //method1 will execute at pageload
  },
  methods:{
    async getData(){
      try {
        var accesstoken = sessionStorage.getItem('token');
        const result = await axios.get('http://localhost:4000/studDeatils', {
          headers: {
            Authorization: 'Bearer ' + accesstoken //the token is a variable which holds the token
          }
        });
        if(result.data != ''){
          this.studentData.studDetails = result.data;
          console.log(this.studentData.studDetails._id);
        }       
      } catch (error) {
        console.log(error);
      }
    },
    addStudent() {
       Router.push('/studentRegistration');
    },
    async deleteStudent(stud, studId){
      try {
        const result = await axios.delete(`http://localhost:4000/students/${studId}`);
        console.log(result);
        this.getData();
      } catch (error) {
        console.log(error);
      }
    },
    updateStudentDetails(){
      Router.push('/studentRegistration');
    }
  }
};
</script>
