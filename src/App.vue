<template>
<div id="app">
  <first-page />
  
</div>
  <!-- <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </nav>
  <router-view/> -->
</template>


<script>
  import FirstPage from './components/FirstPage.vue'


  export default{
    components: { FirstPage },

  }

  
</script>

<style>
#app {
  font-family: 'Open Sans', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: #FFE766;
  padding: 30px 280px;
  height: 100%;
}

.form-main-wraper h1{
  font-family: 'Comfortaa', cursive;
  color: #483698;
  font-weight: bolder;
  font-size: 2.2em;
  letter-spacing: 1px;
}


.form-main-wraper h2{
  font-family: 'Open Sans', sans-serif;
  font-size: 25px;
  margin: 30px 0;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}

.back-arrow{
  
}
</style>
