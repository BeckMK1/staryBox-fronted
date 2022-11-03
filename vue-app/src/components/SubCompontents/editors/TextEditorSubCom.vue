<template>
    <div>
      <div class="editorContainer">
          <div class="langContainer">
          <div :class="showDa == true ? 'langActive' : ''" class="lang" @click="showDa = true, showEn = false">
              <span>da</span>
          </div>
          <div :class="showEn == true ? 'langActive' : ''" class="lang" @click="showDa = false, showEn = true">
              <span>en</span>
          </div>
      </div>
      <div v-if="showDa == true" class="editorWrapper">
      <label for="">Tekst </label>
      <textarea v-model="textDa" class="editor" cols="30" rows="10"></textarea>
      </div>
      <div v-if="showEn == true" class="editorWrapper">
      <label for="">Tekst </label>
      <textarea v-model="textEn" class="editor" cols="30" rows="10"></textarea>
      </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
  data(){
      return{
              textDa:'',
              textEn:'',
          showDa:true,
          showEn:false
      }
  },
  watch:{
      textDa(newText, oldText){
          if(newText != oldText){
              this.$emit('sendTextDa', this.textDa)
              console.log('sent')
          }
      },
      textEn(newText, oldText){
          if(newText != oldText){
              this.$emit('sendTextEn', this.textEn)
              console.log('sent')
          }
      },
  }
  }
  </script>
  
  <style lang="scss" scoped>
  @import "../../../assets/styles/editorStyles.scss";
  </style>