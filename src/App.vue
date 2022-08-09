<template>
  <Navbar :logo="logo_src" :alt="app_name" />
  <router-view/>
  <Footer />
</template>

<script>
import Navbar from './components/Navbar.vue'
import Footer from './components/Footer.vue'

  export default{
    components:{
      Navbar,
      Footer,
    },
    data(){
      return{
        logo_src: '/img/logo.png',
        app_name: 'Make Your Burger',
      }
    }
  }
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,300;0,400;0,500;1,100;1,300;1,400;1,500&display=swap');

  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Roboto', sans-serif;
  }

  h1{
    text-align: center;
    margin-top: 5%;
    font-size: 30pt;
  }

  .main-container {
    margin: 50px;
    min-height: 250px;
  }
</style>
