<template>
  <div class="wrap">
    <ul class="listmenu" :style="listmenustyle" @mouseout="show=false">
      <slot name="menu" v-for="(item,index) in menu_datas" @mouseover="displayChildMenu(index)" :item=item :index=index></slot>
    </ul>
    <transition name="childmenu">
      <ul v-show="show" class="childmenu" :style="childmenustyle" @mouseover="show=true" @mouseout="show=false">
        <slot name="childmenu" v-for="citem in menu_datas[inx]['childcontent']" :item=citem></slot>
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
        left: (parseInt(this.width)-0.01)+"vw"

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
    }
    .childmenu{
      @include flex(column ,flex-start);
      position: absolute;
      background-color: rgb(237, 249, 249);
      width:50vw;
      overflow: auto;
      box-shadow: 5px 5px 5px #888888;
      top: 0;
      &.childmenu-enter-active, &.childmenu-leave-active {
        transition: width .5s;
      }
      &.childmenu-enter, &.childmenu-leave-to {
        width: 0px;
      }
    }
}



</style>
