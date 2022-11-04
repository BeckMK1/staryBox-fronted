<template>
  <div class="blockContainer">
    <div class="langContainer">
        <span v-for="(lang, index) in langs" :key="{index}" @click="isSaved(lang)"  :class="selectedLang == lang ? 'langSelected' : ''">{{lang}}</span>
    </div>
    <div class="editorContainer" v-for="(lang, index) in langs" :key="index" v-show="selectedLang == lang">
    <image-editor-com @sendImage="getImage"></image-editor-com>
    <text-editor-sub-com @sendText="getText"></text-editor-sub-com>
    </div>
    <div class="blockPreview textImage" :class="'blockPreview'+lang" v-for="(lang, index) in langs" :key="index" v-show="selectedLang == lang"  >
        <img :src="image" alt="">
        <p class="text" >{{text}}</p>
    </div>
    <div class="warnMessage" v-if="isWran == true">
       <span>du skal gemme før du ændre sprog</span> 
        <i class="fa-solid fa-arrow-down"></i>
    </div>
  </div>
</template>

<script>
import ImageEditorCom from '../editors/imageEditorCom.vue'
import TextEditorSubCom from '../editors/TextEditorSubCom.vue'


export default {
  components: { TextEditorSubCom, ImageEditorCom,   },
  props:{
    dataSaved:{
        type:Boolean,
        default:false
    }
  },
data(){
    return{
        text:"",
        image:"",
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
    }
   } 
},
methods:{
    getImage(data){
        this.image = data
        this.blockUpdated = true
        this.$emit('sendSave', this.saveData)
    },
    getText(data){
        this.text = data
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