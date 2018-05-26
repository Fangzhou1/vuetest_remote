<template>
  <div id="app">
    <hder></hder>
    <slide></slide>
    <route-view></route-view>


  </div>
</template>

<script>
import hder from '@/page/header';
import btn from '@/components/button';
import slide from '@/components/slide';
export default {
  name: 'App',
  components: {
    hder,
    slide
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}
</style>
