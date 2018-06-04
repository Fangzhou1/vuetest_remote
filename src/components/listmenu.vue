<template>

    <ul class="listmenu" :style="listmenustyle">
      <li>12313123</li>
      <li>12313123</li>
      <li>12313123</li>
      <li>12313123</li>
      <li>12313123</li>
      <li>12313123</li>
    </ul>


</template>

<script>
export default {
  data () {
    return {
      listmenustyle: {
        backgroundColor: this.background_color,
        width: this.width,
        height: this.height
      }
      // listmenustyle: {
      //   backgroundColor:"rgb(44, 70, 56)",
      //   width: "400px",
      //   height: "700px"
      // }
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
.listmenu{
  @include flex(column ,space-around);
  li{
    @include li(42px,0,10px,10px);
    color:rgb(132, 212, 31)
  }


}

</style>
