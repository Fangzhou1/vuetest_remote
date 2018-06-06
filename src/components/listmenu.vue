<template>
  <div class="wrap">
    <ul class="listmenu" :style="listmenustyle" @mouseout="show=false">
      <li v-for="(item,index) in menu_datas"@mouseover="displayChildMenu(index)" :key="item.id" v-text="item.content"></li>
    </ul>
    <transition name="childmenu">
      <ul v-show="show" class="childmenu" :style="childmenustyle" @mouseover="show=true" @mouseout="show=false">
        <li v-for="citem in menu_datas[inx]['childcontent']">{{citem.title}}</li>
      </ul>
    </transition>
  </div>
</template>

<script>
export default {
  data () {
    return {
      listmenustyle: {
        backgroundColor: this.background_color,
        width: this.width,
        height: this.height
      },
      childmenustyle: {

        height: this.height,
        left: (parseInt(this.width)-1)+"vw"

      },
      show:false,
      inx:0
    }
  },
  props: {
    width: {
      type:String,
      default () {
        return "0px"
      }
    },
    height:{
      type:String,
      default () {
        return "auto"
      }
    },
    background_color:{
      type:String,
      default () {
        return ''
      }
    },
    menu_datas: {
      type: Array,
      default () {
        return []
      }
    }
  },
  methods: {
    displayChildMenu(index){
      this.show = true;
      this.inx=index;

    }
  }
}
</script>

<style lang="scss" scoped>
@import '~@/assets/css/mixin';
.wrap {
  position: relative;
    .listmenu{
      @include flex(column ,center,stretch);
      width: 10vw;
      overflow: auto;
      li{
        @include li(8vh,0,10px,10px);
        color:rgb(132, 212, 31);
        text-align:center;
      }
    }
    .childmenu{
      @include flex(column ,flex-start);
      position: absolute;
      background-color: rgb(237, 249, 249);
      width:50vw;
      overflow: auto;
      box-shadow: 5px 5px 5px #888888;
      top: 0;
      &.childmenu-enter-active, .childmenu-leave-active {
        transition: width .5s;
      }
      &.childmenu-enter, .childmenu-leave-to {
        width: 0px;
      }
        li{
          @include li(14vh,0,0px,10px);
          color:rgb(8, 8, 7)
        }
    }
}



</style>
