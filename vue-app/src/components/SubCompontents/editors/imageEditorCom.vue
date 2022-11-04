<template>
    <div class="imageEditor inputEditor">
      <div class="editorContainer inputEditorContainer">
      <div v-show="show == true" class="editorWrapper">
        <label for="">billede</label>
        <input v-model="image" type="url" placeholder="billede url">
      </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
  data(){
      return{
          image:'',
          show:true,
      }
  },
  watch:{
    image(newText, oldText){
          if(newText != oldText){
              this.$emit('sendImage', this.image)
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