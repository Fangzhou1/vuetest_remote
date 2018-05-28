<template>
<div id="app">
  <hder></hder>
  <slide :images="images"></slide>
  <route-view></route-view>
</div>
</template>
<script>
import hder from '@/page/header'
import slide from '@/components/slide'
import axios from 'axios'
export default {
  name: 'App',
  data () {
    return {
      images: []
    }
  },
  components: {
    hder,
    slide
  },
  created () {
    var that=this;
    axios.get('/api/static/api/swider.js')
      .then(function (response) {
        that.images = response.data,
        console.log(response.data)
      })
      .catch(function (error) {
        console.log(error)
      })
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
