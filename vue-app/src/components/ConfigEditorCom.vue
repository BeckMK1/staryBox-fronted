<template>
    <div>
        <config-block-meta></config-block-meta>
      <text-editor-sub-com @sendTextDa="getTextDa" @sendTextEn="getTextEn" v-if="isTextEditor == true" ></text-editor-sub-com>
      <html-editor-sub-com-vue v-if="isHtmlEditor == false" ></html-editor-sub-com-vue>
      <transition>
        <save-editor-sub-com v-if="showSave == true"></save-editor-sub-com>
      </transition>
    </div>
    </template>
    
    <script>
    import ConfigBlockMeta from './ConfigBlockMeta.vue'
    import SaveEditorSubCom from './SubCompontents/SaveEditorSubCom.vue'
    import TextEditorSubCom from './SubCompontents/TextEditorSubCom.vue'
    import HtmlEditorSubComVue from './SubCompontents/HtmlEditorSubCom.vue'
    export default {
      components: { TextEditorSubCom, SaveEditorSubCom, ConfigBlockMeta, HtmlEditorSubComVue },
      name: 'ConfigEditorCom',
      data(){
        return{
          TextData:{
            textDa:'',
            textEn:'',
          },
          showSave:false,
          isTextEditor:true,
          isHtmlEditor:true
        }
      },
      methods:{
        getTextDa(data){
        this.TextData.textDa = data
        this.showSave=true
        },
        getTextEn(data){
        this.TextData.textDa = data
        this.showSave=true
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
    </style>