<template>
  <div class="home">
   <!-- <img alt="Vue logo" src="../assets/logo.png" />-->
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <span>Welcome {{name}}</span>
    <!-- bind a class -->
    <div v-html='desg' v-bind:class='desgClass'></div>
    <!--bind ID -->
    <div v-html ='msg' v-bind:id='msgID'></div>
    <!--add class by checking isPromoted is true-->
    <div v-bind:class = "isPromoted && 'promoted'">Promoted movies</div>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "Home",
  components: {
   // HelloWorld,
  },
  data(){
    return{
      name: 'jasmin Mathew',
      desg: '<b>software eng</b>',
      msg: `<a href="#" onClick = "alert ('hi') "> Read More </a>`,
      msgID: 'itemmsg',
      desgClass: 'designation',
      isPromoted: 'false'
    }

  },
};
</script>
<style>
.promoted {
  font-style: italic;
}
</style>
