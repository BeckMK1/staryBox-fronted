<template>
  <div class="blockContainer">
    <div class="editorContainer">
    <text-string-editor @sendTextStringDa="getTitleDa"></text-string-editor>
    <text-editor-sub-com @sendTextDa="getTextDa"></text-editor-sub-com>
    <link-editor-com @sendLinkDa="getLinkDa"></link-editor-com>
    </div> 
    <div class="blockPreview">
        <div class="title"></div>
        <p class="text"></p>
        <div class="link"></div>
    </div>
  </div>
</template>

<script>
import LinkEditorCom from '../editors/LinkEditorCom.vue'
import TextEditorSubCom from '../editors/TextEditorSubCom.vue'
import TextStringEditor from '../editors/TextStringEditor.vue'

export default {
  components: { TextEditorSubCom, TextStringEditor, LinkEditorCom },
data(){
    return{
        titleDa:"",
        textDa:"",
        linkDa:"",
        titleEn:"",
        textEn:"",
        linkEn:"",
        saveData:true
    }
},
methods:{
    getTitleDa(data){
        const preview = document.querySelector(".blockPreview .title");
        this.titleDa = data
        preview.innerHTML = this.titleDa
        this.$emit('sendSave', this.saveData)
    },
    getTextDa(data){
        const preview = document.querySelector(".blockPreview p");
        this.textDa = data
        preview.innerHTML = this.textDa
        this.$emit('sendSave', this.saveData)
    },
    getLinkDa(data){
        const preview = document.querySelector(".blockPreview .link");
        this.linkDa = data
        preview.innerHTML = this.linkDa
        this.$emit('sendSave', this.saveData)
    },
    }
}
</script>

<style lang="scss" scoped>
@import "../../../assets/styles/blockStyles.scss";
</style>