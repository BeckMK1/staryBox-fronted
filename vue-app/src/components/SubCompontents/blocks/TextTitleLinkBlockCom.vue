<template>
  <div class="blockContainer">
    <div class="langContainer">
        <span v-for="(lang, index) in langs" :key="{index}" @click="isSaved(lang)"  :class="selectedLang == lang ? 'langSelected' : ''">{{lang}}</span>
    </div>

    <div class="editorContainer" v-for="(lang, index) in langs" :key="index" v-show="selectedLang == lang">
        <text-string-editor @sendTextString="getTitle"></text-string-editor>
        <text-editor-sub-com @sendText="getText"></text-editor-sub-com>
        <link-editor-com @sendLink="getLink"></link-editor-com>
    </div>

    <div class="blockPreview" :class="'blockPreview'+lang" v-for="(lang, index) in langs" :key="index" v-show="selectedLang == lang"  >
        <div class="title" v-html="title"></div>
        <p class="text" >{{text}}</p>
        <div class="link" v-html="link"></div>
    </div>

    <div class="warnMessage" v-if="isWran == true">
        <span>du skal gemme før du ændre sprog</span> 
        <i class="fa-solid fa-arrow-down"></i>
    </div>
  </div>
</template>

<script>
import LinkEditorCom from '../editors/LinkEditorCom.vue'
import TextEditorSubCom from '../editors/TextEditorSubCom.vue'
import TextStringEditor from '../editors/TextStringEditor.vue'

export default {
  components: { TextEditorSubCom, TextStringEditor, LinkEditorCom,  },
  props:{
    dataSaved:{
        type:Boolean,
        default:false
    }
  },
data(){
    return{
        title:"",
        text:"",
        link:"",
        blockUpdated:false,
        saveData:true,
        isWran:false,
        selectedLang: "da",
        langs:[
            'da',
            'en'
        ]
    }
},
watch:{
    dataSaved(newData){
    if(newData == true){
        this.blockUpdated = false
        console.log('saved')
        this.title = ''
        this.text=''
        this.link=''
    }
   }, 
},
methods:{
    getTitle(data){
        this.title = data
        this.blockUpdated = true
        this.$emit('sendSave', this.saveData)
    },
    getText(data){
        this.text = data
        this.blockUpdated = true
        this.$emit('sendSave', this.saveData)
    },
    getLink(data){
        this.link = data
        this.blockUpdated = true
        this.$emit('sendSave', this.saveData)
    },
    isSaved(data){
        if(this.dataSaved == true || this.blockUpdated == false ){
            this.selectedLang = data
        }else{
            this.isWran = true
        }
    }
    }
}
</script>

<style lang="scss" scoped>
@import "../../../assets/styles/blockStyles.scss";
</style>