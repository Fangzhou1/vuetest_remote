<template>
  <div class="wrap">
    <ul class="listmenu" :style="listmenustyle">
      <li>12313123</li>
      <li>12313123</li>
      <li>12313123</li>
      <li>12313123</li>
      <li>12313123</li>
      <li>12313123</li>
    </ul>
    <ul v-show="show" class="childmenu" :style="childmenustyle">
      <li>1234567</li>
      <li>1234567</li>
      <li>1234567</li>
      <li>1234567</li>
      <li>1234567</li>
      <li>1234567</li>
      <li>1234567</li>
      <li>1234567</li>
      <li>1234567</li>
      <li>1234567</li>
      <li>1234567</li>
      <li>1234567</li>
      <li>1234567</li>
      <li>1234567</li>
      <li>1234567</li>
      <li>1234567</li>
      <li>1234567</li>
      <li>1234567</li>
      <li>1234567</li>
      <li>1234567</li>
      <li>1234567</li>
      <li>1234567</li>
      <li>1234567</li>
      <li>1234567</li>
    </ul>
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
        left: this.width,

      },
      show: true
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
    datas: {
      type: Array,
      default () {
        return []
      }
    }
  }
}
</script>

<style lang="scss" scoped>
@import '~@/assets/css/mixin';
.wrap {
  position: relative;
    .listmenu{
      @include flex(column ,space-around);
      width: 10vw;
      li{
        @include li(8vh,0,10px,10px);
        flex:1;
        color:rgb(132, 212, 31)
      }
    }
    .childmenu{
      @include flex(column ,flex-start);
      position: absolute;
      background-color: rgb(237, 249, 249);
      border: 1px solid rgb(8, 8, 7);
      width:auto;
      top: 0;
        li{
          @include li(14vh,0,0px,10px);
          color:rgb(8, 8, 7)
        }
    }
}



</style>
