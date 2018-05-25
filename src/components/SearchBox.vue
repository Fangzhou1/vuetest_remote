<template>
<div>
  <input type="text" name="" value="">

</div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
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
    height: 40px;
    background-color: rgb(21, 21, 23);
    .header-left {
        @include flex(row,flex-start,center);
        margin-left: 5%;
        li {
            @include li(20px,1,10px)
        }
    }
    .header-right {
        @include flex(row,flex-start,center);
        margin-right: 5%;
        li {
            @include li(20px,1,10px)
        }
    }

}

</style>
