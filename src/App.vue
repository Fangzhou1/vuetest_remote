<template>
<div id="app">
  <hder></hder>
  <hder2></hder2>
  <!-- <slide :images="images"></slide> -->
  <listmenu ref="listmenu" :listmenuData="listmenuData" :listmenuStyle="listmenuStyle">
      <li slot="menu" slot-scope="props" class="menu" :key="props.item.id" @mouseover="displayChildMenu(props.index)"><span v-text="props.item.content"></span></li>
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
      listmenuStyle: {
        width:"20vw",
        height:"70vh",
        background_color:"rgba(34, 40, 20,0.5)"
      },
      listmenuData:[],
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
          this.listmenuData = response.data
           console.log(typeof response.data)
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
    @include li(14vh,0,0px,10px);
    color:rgb(8, 8, 7)
  }
  /* margin-top: 60px; */
}
</style>
