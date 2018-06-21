<template>
<div class="header2meauwrap">
  <div class="brand">
    <img src="../assets/image/xmlogo.jpg" alt="">
  </div>
  <header2meau id="header2meau" ref="header2meau" :data="" :listmenuData="this.listmenuData" :listmenuStyle="this.listmenuStyle">
    <li slot="menu" slot-scope="props" class="menu" :key="props.item.id" @mouseover="displayChildMenu(props.index)">{{props.item.content}}</li>
    <li slot="childmenu" slot-scope="props" class="listmenu" :key="props.item.id"><img :src="props.item.image" width="40px" height="40px"/>{{props.item.title}}</li>
  </header2meau>
  <div class="searchbox">

  </div>
</div>
</template>

<script>
import header2meau from '@/components/listmenu'
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
        height: this.listmenuStyle.height,
        left: (parseInt(this.width)-0.01)+"vw",
        flexDirection: this.flexDirection
      },
      listmenuData:[],
    }
  },
  components: {
    header2meau
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
          console.log(response.data)
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
  .brand{
    background:url("../assets/image/xmlogo.jpg") no-repeat ;
    margin-left: 20px;
  }
  #header2meau{
    li.menu{
      list-style:none;
      cursor: pointer


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
