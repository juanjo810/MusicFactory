<template>
  <div id="app">
    <router-link to="/dashboard">
      <img src="@/assets/logo.jpg">
    </router-link>
    <router-view class="container"/>
  </div>
</template>

<script>

export default {
  name: 'App'
}
</script>

<style>
  body{
    background-color: #456;
  }
  img{
    width:5%;
    float: left;
    padding: 1%
  }

  #app {
    padding: 0;
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
  }

  .container{
    padding-bottom: 4rem;
  }
</style>
