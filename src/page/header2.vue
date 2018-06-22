<template>
<div class="header2meauwrap">
  <div class="brand">
    <img src="../assets/image/xmlogo.jpg" alt="">
  </div>
  <header2meau id="header2meau" ref="header2meau" :listmenuData="listmenuData" :listmenuStyle="listmenuStyle" :childmenuStyle="childmenuStyle">
    <li slot="menu" slot-scope="props" class="menu" @mouseover="displayChildMenu(props.index)" :key="props.item.id"><span v-text="props.item.content"></span></li>
    <li slot="childmenu" slot-scope="props" class="listmenu" :key="props.item.id"><div><img :src="props.item.image" width="40px" height="40px"/></div><span v-text="props.item.title"></span></li>
  </header2meau>
  <div class="searchbox">
    <search-box></search-box>
  </div>
</div>
</template>

<script>
import header2meau from '@/components/listmenu'
import searchBox from '@/components/searchBox'
import axios from 'axios'
export default {
  data () {
    return {
      listmenuStyle: {
        width:"47vw",
        height:"13.8vh",
        backgroundColor:"yellow",
        flex_direction:"row",
        justify_content:"space-around",
        align_items: "center"
      },
      childmenuStyle: {
        width:"100vw",
        height: "30vh",
        left:0,
        top:"8vh",
        flexDirection: "row",
        justify_content:"space-around"
      },
      listmenuData:[]
    }
  },
  components: {
    header2meau,
    searchBox
  },
  created () {
    // this.getSliderData();
    this.getHeader2meauData();

  },
  methods: {
    getHeader2meauData () {
      axios.get('/api/static/api/menuheaderdatas.js')
        .then((response) => {
          this.listmenuData = response.data
           // console.log(response.data)
        })
        .catch(function (error) {
          console.log(error)
        })
    },
    displayChildMenu(index) {
      this.$refs.header2meau.displayChildMenu(index)
    }
  }
}
</script>

<style lang="scss" scoped>
@import '~@/assets/css/mixin';
.header2meauwrap{
  @include flex(row,space-between);
  position:relative;
  .brand{
    background:url("../assets/image/xmlogo.jpg") no-repeat ;
    margin-left: 20px;
  }
  #header2meau{
    position: static;
    li.menu{
      list-style:none;
      cursor: pointer;
      flex-grow:1
    }
    li.listmenu{
      @include flex(column,center,center);
      @include li(22vh,1);
      line-height: 10vh;
      overflow: hidden;
      flex:1 1 auto;



    }
  }

}

// .header-one {
//     @include flex(row,space-between);
//     color: rgb(145, 156, 148);
//     width:100%;
//     min-height: 40px;
//     height: auto;
//     background-color: rgb(21, 21, 23);
//     .header-left {
//         @include flex(row,flex-start,center);
//         margin-left: 5%;
//         li {
//             @include li(20px,1,0px,10px)
//         }
//     }
//     .header-right {
//         @include flex(row,flex-start,center);
//         margin-right: 5%;
//         li {
//             @include li(20px,1,0px,10px)
//         }
//     }
//
// }

</style>
