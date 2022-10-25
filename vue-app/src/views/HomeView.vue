<template>
  <div class="home container">
    <div class="">
      <config-com></config-com>
    </div>
  </div>
</template>

<script>
import ConfigCom from '@/components/ConfigCom.vue'
// @ is an alias to /src

export default {
  components: { ConfigCom },
  name: 'HomeView',
}
</script>
<style lang="scss" scoped>
.test{
background: red;
height: 100vh;
}
</style>