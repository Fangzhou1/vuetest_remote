<template>
  <div >
    <div class="btn">
    123
    </div>
  </div>

</template>

<script>
export default {
  data() {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<style lang="scss" scoped>
@import '~@/assets/css/mixin';
.btn{
  @include btn(white,black,45px,45px);

}


</style>
