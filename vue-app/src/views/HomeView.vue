<template>
  <div class="home container">
    <div class="">
      <config-list-com></config-list-com>
    </div>
  </div>
</template>

<script>
import ConfigListCom from '@/components/ConfigListCom.vue'
// @ is an alias to /src

export default {
  name: 'HomeView',
  components: {
    ConfigListCom
  }
}
</script>
<style lang="scss" scoped>
.test{
background: red;
height: 100vh;
}
</style>