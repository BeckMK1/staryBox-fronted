<template>
    <div class="imageEditor inputEditor">
      <div class="editorContainer inputEditorContainer">
          <div class="langContainer">
          <div :class="showDa == true ? 'langActive' : ''" class="lang" @click="showDa = true, showEn = false">
              <span>da</span>
          </div>
          <div :class="showEn == true ? 'langActive' : ''" class="lang" @click="showDa = false, showEn = true">
              <span>en</span>
          </div>
      </div>
      <div v-show="showDa == true" class="editorWrapper">
        <label for="">billede</label>
        <input v-model="imageDa" type="url" placeholder="billede url">
      </div>
      <div v-show="showEn == true" class="editorWrapper">
        <label for="">billede</label>
        <input v-model="imageEn" type="url" placeholder="billede url">
      </div>
      </div>
      <p>preview</p>
      <div class="preview" v-show="showDa == true" >
        <img :src="imageDa" alt="">
      </div>
      <div class="preview" v-show="showEn == true">
        <img :src="imageEn" alt="">
      </div>
    </div>
  </template>
  
  <script>
  export default {
  data(){
      return{
          imageDa:'',
          imageEn:'',
          showDa:true,
          showEn:false
      }
  },
  watch:{
    imageDa(newText, oldText){
          if(newText != oldText){
              this.$emit('sendImageDa', this.imageDa)
              console.log('sent')
          }
      },
      imageEn(newText, oldText){
          if(newText != oldText){
              this.$emit('sendImageEn', this.imageEn)
              console.log('sent')
          }
      },

  },
  methods:{
    }
  }
  </script>
  
  <style lang="scss" scoped>
  @import "../../../assets/styles/editorStyles.scss";
  </style>