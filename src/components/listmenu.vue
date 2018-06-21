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
        backgroundColor: this.listmenuStyle.background_color,
        width: this.listmenuStyle.width,
        height: this.listmenuStyle.height,
        flexDirection: this.listmenuStyle.flex_direction,
        justifyContent:this.listmenuStyle.justify_content,
        alignItems:this.listmenuStyle.align_items
      },
      childmenustyle: {
        width:this.childmenuStyle.width,
        height: this.childmenuStyle.height,
        left: this.childmenuStyle.left,
        flexDirection: this.childmenuStyle.flexDirection
      },
      show:false,
      inx:0
    }
  },
  props: {
    listmenuStyle:{
      type: Object,
      default: function () {
        return {
          width: "0px",
          height: "auto",
          background_color:'',
          flex_direction: "column",
          justify_content: "center",
          align_items: "center"
          }
        }
      },
      childmenuStyle:{
        type: Object,
        default: function () {
          return {
            width: this.listmenuStyle.width,
            height: this.listmenuStyle.height,
            left: (parseInt(this.width)-0.01)+"vw",
            flexDirection: this.listmenuStyle.flex_direction
            }
          }
        },
    menu_datas: {
      type: Array,
      default: []
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
