<template>
  <div class="container transitionContainer">
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
import ConfigListCom from './ConfigListCom.vue'
export default {
  components: { ConfigListCom, ConfigBlockCom },
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