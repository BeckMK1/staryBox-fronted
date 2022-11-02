<template>
    <div>
      <div class="editorContainer">
        <config-block-meta></config-block-meta>
      <text-editor-sub-com @sendTextDa="getTextDa" @sendTextEn="getTextEn" v-if="isTextEditor == true" ></text-editor-sub-com>
      <html-editor-sub-com-vue @sendHtmlDa="getHtmlDa" @sendHtmlEn="getHtmlEn" v-if="isHtmlEditor == true" ></html-editor-sub-com-vue>
      <image-editor-com @sendImageDa="getImageDa" @sendImageEn="getImageEn" v-if="isImageEditor == true"></image-editor-com>
      <link-editor-com v-if="isLinkEditor == true"></link-editor-com>
      <text-string-editor v-if="isTextStringEditor == true"></text-string-editor>
    </div>
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
import ImageEditorCom from './SubCompontents/editors/imageEditorCom.vue'
import LinkEditorCom from './SubCompontents/editors/LinkEditorCom.vue'
import TextStringEditor from './SubCompontents/editors/TextStringEditor.vue'
    export default {
      components: { TextEditorSubCom, SaveEditorSubCom, ConfigBlockMeta, HtmlEditorSubComVue, ImageEditorCom, LinkEditorCom, TextStringEditor },
      name: 'ConfigEditorCom',
      data(){
        return{
          TextData:{
            textDa:'',
            textEn:'',
          },
          htmlData:{
            htmlDa:'',
            textEn:''
          },
          imageData:{
            imageDa:'',
            imageEn:''
          },
          showSave:false,
          isTextEditor:false,
          isHtmlEditor:false,
          isImageEditor:false,
          isLinkEditor:false,
          isTextStringEditor:true
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
        },
        getHtmlDa(data){
        this.htmlData.htmlDa = data
        this.showSave=true
        },
        getHtmlEn(data){
        this.htmlData.htmlEn = data
        this.showSave=true
        },
        getImageDa(data){
        this.imageData.imageDa = data
        this.showSave=true
        },
        getImageEn(data){
        this.imageData.imageEn = data
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
    .editorContainer{
      padding-bottom: 50px;
    }
    </style>