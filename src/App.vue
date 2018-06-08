<template>
<div id="app">
  <hder></hder>
  <hder2></hder2>
  <!-- <slide :images="images"></slide> -->
  <listmenu ref="listmenu" :menu_datas="listmenuProps.menudata" :width="listmenuProps.width" :height="listmenuProps.height" :background_color="listmenuProps.backgroundColor">
      <li slot="menu" slot-scope="props" class="menu" :key="props.item.id" @mouseover="displayChildMenu(props.index)">{{props.item.content}}</li>
      <li slot="childmenu" slot-scope="props" class="listmenu" :key="props.item.id"><img :src="props.item.image" width="40px" height="40px"/>{{props.item.title}}</li>
  </listmenu>
  <route-view></route-view>
</div>
</template>
<script>
import hder from '@/page/header'
import hder2 from '@/page/header2'
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
    hder2,
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
    },
    displayChildMenu(index) {
      this.$refs.listmenu.displayChildMenu(index)
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
  li.menu{
    @include li(8vh,0,10px,10px);
    color:rgb(132, 212, 31);
    text-align:center;
  }
  li.listmenu{
    @include flex(row,center);
    @include li(14vh,0,0px,10px);
    color:rgb(8, 8, 7)
  }
  /* margin-top: 60px; */
}
</style>
