<template>
<div id="app">
  <hder></hder>
  <!-- <slide :images="images"></slide> -->
  <listmenu :menu_datas="menudata" :width="width" :height="height" :background_color="backgroundColor">
    <!-- <template slot-scope="props">
      {{props.item.title}}
    </template> -->
  </listmenu>
  <route-view></route-view>
</div>
</template>
<script>
import hder from '@/page/header'
// import slide from '@/components/slide'
import listmenu from '@/components/listmenu'
import axios from 'axios'
export default {
  name: 'App',
  data () {
    return {
      images: [],
      width:"20vw",
      height:"70vh",
      backgroundColor:"rgba(34, 40, 20,0.5)",
      menudata:[]
    }
  },
  components: {
    hder,
    listmenu

  },
  created () {
    // this.getSliderData();
    this.getMenuData();

  },
  methods: {
    // getSliderData () {
    //   axios.get('/api/static/api/swider.js')
    //     .then((response) => {
    //       this.images = response.data;
    //     })
    //     .catch(function (error) {
    //       console.log(error)
    //     })
    // },
    getMenuData () {
      axios.get('/api/static/api/menudatas.js')
        .then((response) => {
          this.menudata = response.data
          // console.log(response.data)
        })
        .catch(function (error) {
          console.log(error)
        })
    }
  }

}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  /* margin-top: 60px; */
}
</style>
