<template>
    <div class="inputEditor">
      <div class="editorContainer inputEditorContainer linkEditorContainer">
          <div class="langContainer">
          <div :class="showDa == true ? 'langActive' : ''" class="lang" @click="showDa = true, showEn = false">
              <span>da</span>
          </div>
          <div :class="showEn == true ? 'langActive' : ''" class="lang" @click="showDa = false, showEn = true">
              <span>en</span>
          </div>
      </div>
      <div v-show="showDa == true" class="editorWrapper">
        <label for="">Link</label>
        <input v-model="linkDa" type="url" placeholder="url">
        <input v-model="linkTextDa" type="url" placeholder="url tekst">
        <div class="checkboxContainer">
            <label for="">åben i ny fane</label>
            <input type="checkbox" @click="fanDa = !fanDa">
        </div>
      </div>
      <div v-show="showEn == true" class="editorWrapper">
        <label for="">Link</label>
        <input v-model="linkEn" type="url" placeholder="url">
        <input v-model="linkTextEn" type="url" placeholder="url tekst">
        <div class="checkboxContainer">
            <label for="">åben i ny fane</label>
            <input type="checkbox" @click="fanEn = !fanEn">
        </div>
      </div>
      </div>
      <p>preview</p>
      <div class="preview" v-show="showDa == true" >
        <a :href="linkDa" :target="fanDa == true ? '_blank' : ''">{{linkTextDa}}</a>
      </div>
      <div class="preview" v-show="showEn == true">
        <a :href="linkEn" :target="fanDa == true ? '_blank' : ''">{{linkTextEn}}</a>
      </div>
    </div>
  </template>
  
  <script>
  export default {
  data(){
      return{
          linkDa:'',
          linkTextDa:'',
          fanDa:false,
          linkEn:'',
          linkTextEn:'',
          fanEn:false,
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