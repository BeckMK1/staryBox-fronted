<template>
  <div class="metaContainer">
    <div class="metaInput">
        <conifg-input-com @sendInput="getData" label="Page id" size="50px"></conifg-input-com>
        <conifg-input-com @sendInput="getData" label="Parent id" size="50px"></conifg-input-com>
        <conifg-input-com @sendInput="getData" label="Oprettet" size="200px"></conifg-input-com>
        <conifg-input-com @sendInput="getData" label="sidst opdateret" size="200px" ></conifg-input-com>
        <conifg-input-com @sendInput="getData" label="domæne" size="250px" ></conifg-input-com>
        <conifg-input-com @sendInput="getData" label="Created by" size="50px"></conifg-input-com>
        <conifg-input-com @sendInput="getData" label="Template id" size="50px"></conifg-input-com>
    </div>
    <div class="metaInput">
        <conifg-input-com @sendInput="getData" label="Name" size="132px"></conifg-input-com>
        <conifg-input-com @sendInput="getData" label="Linkname" size="200px"></conifg-input-com>
        <conifg-input-com @sendInput="getData" label="Filename" size="200px"></conifg-input-com>
        <conifg-input-com @sendInput="getData" label="filetype" :dropdown="true" :options="testOptions" size="75px" ></conifg-input-com>
        <conifg-input-com @sendInput="getData" label="sprog" :dropdown="true" :options="testOptions" size="75px" ></conifg-input-com>
        <conifg-input-com @sendInput="getData" label="visable" :dropdown="true" :options="testOptions" size="75px"></conifg-input-com>
    </div>
    <div class="metaInput">
        <conifg-input-com @sendInput="getData" label="seo ord" size="300px"></conifg-input-com>
    </div>
    <div class="btns">
    <button>Udgiv <i class="fa-solid fa-cloud-arrow-up"></i></button>
    <button>publicer</button>
    </div>
  </div>
</template>

<script>
import ConifgInputCom from './SubCompontents/ConifgInputCom.vue'
export default {
  components: { ConifgInputCom },
name:"ConfigMeta",
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
    margin-bottom:32px;
    position: relative;
    .metaInput{
        display: flex;
        gap:32px;
        margin-bottom:8px;
    }
    .btns{
        position: absolute;
        right:32px;
        bottom: 12px;
        button{
            display: block;
            &:last-child{
                margin-top:8px;
                border:black solid 2px;
            }
        }
    }
}

</style>