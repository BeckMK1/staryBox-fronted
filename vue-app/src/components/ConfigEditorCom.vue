<template>
    <div>
      <config-block-meta></config-block-meta>
      <div class="editorContainer">
       <text-image-block-com :dataSaved="save" @sendSave="getSave"></text-image-block-com>
    </div>
      <transition>
        <save-editor-sub-com @sendSave="setSave" v-if="showSave == true"></save-editor-sub-com>
      </transition>
    </div>
    </template>
    
    <script>
import TextImageBlockCom from './SubCompontents/blocks/TextImageBlockCom.vue'
    import SaveEditorSubCom from './SubCompontents/SaveEditorSubCom.vue'
    import ConfigBlockMeta from './ConfigBlockMeta.vue'
    export default {
      components: { SaveEditorSubCom, TextImageBlockCom, ConfigBlockMeta  },
      name: 'ConfigEditorCom',
      data(){
        return{
          showSave:false,
          save:false
        }
      },
      methods:{
        getSave(data){
          this.showSave = data
        },
        setSave(data){
          this.save = data
          this.showSave = false
          setTimeout(() => {
            this.save = false
          }, 200);
        }
      }
  }
    </script>
    
    <!-- Add "scoped" attribute to limit CSS to this component only -->
    <style scoped lang="scss">
    .v-enter-active,
    .v-leave-active {
      transform: translateY(0px);
      transition:200ms ease;
    }
    
    .v-enter-from,
    .v-leave-to {
      transform: translateY(50px);
    }
    .editorContainer{
      padding-bottom: 50px;
    }
    </style>