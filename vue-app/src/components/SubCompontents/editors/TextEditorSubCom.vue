<template>
    <div>
      <div class="editorContainer">
      <div class="editorWrapper">
      <label for="">Tekst </label>
      <textarea v-model="text" class="editor" cols="30" rows="10"></textarea>
      </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
  data(){
      return{
              text:'',
      }
  },
  watch:{
      text(newText, oldText){
          if(newText != oldText){
              this.$emit('sendText', this.text)
              console.log('sent')
          }
      },
  }
  }
  </script>
  
  <style lang="scss" scoped>
  @import "../../../assets/styles/editorStyles.scss";
  </style>