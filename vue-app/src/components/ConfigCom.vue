<template>
  <div class="container transitionContainer">
    <config-new-page-com></config-new-page-com>
    <config-block-meta></config-block-meta>
       <button @click="goToBlock=null" class="backBtn" v-if="goToBlock != null"><i class="fa-solid fa-arrow-left-long"></i></button>
    <transition>
        <config-list-com @goToEdit="getData" v-if="goToBlock == null"></config-list-com>
    </transition>
    <transition>
        <config-block-com :showBlock="goToBlock" v-if="goToBlock != null"></config-block-com>
    </transition>
  </div>
</template>

<script>
import ConfigBlockCom from './ConfigBlockCom.vue'
import ConfigBlockMeta from './ConfigBlockMeta.vue'
import ConfigListCom from './ConfigListCom.vue'
import ConfigNewPageCom from './ConfigNewPageCom.vue'
export default {
  components: { ConfigListCom, ConfigBlockCom, ConfigNewPageCom, ConfigBlockMeta },
  data(){
    return{
        goToBlock:null
    }
  },
  methods:{
    getData(data){
    this.goToBlock = data
    }
  }

}
</script>

<style lang="scss" scoped>
.backBtn{
    position: absolute;
    left: 100px;
    background-color: white;
    border:black 1px solid;
    padding: 8px 12px;
    border-radius: 50%;
    transition: 200ms ease;
    i{
            transition: 200ms ease;
    }
    &:hover{
        background-color: black;
        transition: 200ms ease;
        i{
            transition: 200ms ease;
            color:white
        }
    }
}
</style>