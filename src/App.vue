<template>
  <div id="app">
    <header>
      <div class="container row header-wrapper">
        <div id="nav" class="col-sm-10">
          <router-link to="/">Home</router-link> |
          <router-link to="/about">About</router-link> |
          <router-link to="/contactus">Contact Us</router-link> |
          <router-link to="/studentdetails">Student details</router-link>
        </div>
        <div id="login" class="col-sm-2">
        <router-link to="/login">Login</router-link>
        <router-link to="/register">Register</router-link>
        </div>
      </div>
    </header>
    <router-view />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px 0;
  text-align: left;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
  padding: 0 10px;
  text-decoration: none;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
#login{
  text-align: right;
}
#login a{
  padding: 0 10px;
  text-decoration: none;
}
header{    
  border-bottom: 1px solid #ccc;
  margin-bottom: 50px;
}
header .header-wrapper{
  display: flex;
  align-items: center;
  margin: 0 auto !important;
} 

</style>
