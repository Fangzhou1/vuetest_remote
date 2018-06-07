<template>
<div id="app">
  <hder></hder>
  <!-- <slide :images="images"></slide> -->
  <listmenu :menu_datas="listmenuProps.menudata" :width="listmenuProps.width" :height="listmenuProps.height" :background_color="listmenuProps.backgroundColor">
    <template slot-scope="props">
      <li class="listmenu">{{props.item.title}}</li>
    </template>
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
      listmenuProps:{
        width:"20vw",
        height:"70vh",
        backgroundColor:"rgba(34, 40, 20,0.5)",
        menudata:[]
      }
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
          this.listmenuProps.menudata = response.data
          // console.log(response.data)
        })
        .catch(function (error) {
          console.log(error)
        })
    }
  }

}
</script>

<style lang="scss" scoped>
@import '~@/assets/css/mixin';
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  li.listmenu{
    @include li(14vh,0,0px,10px);
    color:rgb(8, 8, 7)
  }
  /* margin-top: 60px; */
}
</style>
