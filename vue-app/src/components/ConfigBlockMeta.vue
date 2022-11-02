<template>
  <div class="metaContainer">
    <div class="metaInput">
        <conifg-input-com label="Block id" ></conifg-input-com>
        <conifg-input-com label="oprettet"></conifg-input-com>
        <conifg-input-com label="sidst opdateret"></conifg-input-com>
        <conifg-input-com label="domæne"></conifg-input-com>
        <conifg-input-com label="created by"></conifg-input-com>
        <conifg-input-com label="template id"></conifg-input-com>
    </div>
    <div class="metaInput">
        <conifg-input-com label="Block Name"></conifg-input-com>
        <conifg-input-com label="Mappe" :dropdown="true"></conifg-input-com>
    </div>
    <button class="saveBtn">gem</button>
  </div>
</template>

<script>
import ConifgInputCom from './SubCompontents/ConifgInputCom.vue'
export default {
  components: { ConifgInputCom },
  data(){
    return{
        metaInputData:null,
        testOptions:[
        "test",
        "test2",
        "test3",
        "test4",
        "test5",
        ]
    }
},
methods:{
    getData(data){
        this.metaInputData = data
    }
}
}
</script>

<style lang="scss" scoped>
.metaContainer{
    border:black solid 2px;
    padding:12px 50px;
    margin-bottom:75px;
    position: relative;
    .metaInput{
        display: flex;
        gap:32px;
        margin-bottom:8px;
    }
    .saveBtn{
        position: absolute;
        right: 32px;
        bottom:8px;
        border: black solid 2px;
    }
}
</style>