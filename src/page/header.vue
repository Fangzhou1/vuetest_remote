<template>
<div>
  <div class="header-top">

  </div>
  <div class="header-one">

    <ul class='header-left'>
      <li>小米商城</li>
      <li>miui</li>
      <li>lot</li>
      <li>云服务</li>
      <li>小爱开放平台</li>
      <li>金融</li>
      <li>有品</li>
      <li>政企服务</li>
      <li>Select Region</li>
    </ul>

    <ul class='header-right'>
      <li>登陆</li>
      <li>注册</li>
      <li>消息通知</li>
      <li>购物车</li>
    </ul>
  </div>
  <div>

  </div>
</div>
</template>

<script>
export default {

  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<style lang="scss" scoped>
@import '~@/assets/css/mixin';
.header-top{
  width:100%;
  height:0px;
  padding-bottom: 6.25%;
  background-position:center center;
  background-image:url(//i1.mifile.cn/a4/cms_15272472755871_QHsJa.jpg);
}
.header-one {
    @include flex(row,space-between);
    color: rgb(145, 156, 148);
    width:100%;
    min-height: 40px;
    height: auto;
    background-color: rgb(21, 21, 23);
    .header-left {
        @include flex(row,flex-start,center);
        margin-left: 5%;
        li {
            @include li(20px,1,0px,10px)
        }
    }
    .header-right {
        @include flex(row,flex-start,center);
        margin-right: 5%;
        li {
            @include li(20px,1,0px,10px)
        }
    }

}

</style>
