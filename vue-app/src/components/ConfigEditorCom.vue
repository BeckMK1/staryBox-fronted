<template>
    <div>
      <div class="editorContainer">
        <text-title-link-block-com @sendSave="getSave" ></text-title-link-block-com>
    </div>
      <transition>
        <save-editor-sub-com v-if="showSave == true"></save-editor-sub-com>
      </transition>
    </div>
    </template>
    
    <script>
    import SaveEditorSubCom from './SubCompontents/SaveEditorSubCom.vue'
    import TextTitleLinkBlockCom from './SubCompontents/blocks/TextTitleLinkBlockCom.vue';
    export default {
      components: { SaveEditorSubCom, TextTitleLinkBlockCom },
      name: 'ConfigEditorCom',
      data(){
        return{
          showSave:false,
        }
      },
      methods:{
        getSave(data){
          this.showSave = data
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