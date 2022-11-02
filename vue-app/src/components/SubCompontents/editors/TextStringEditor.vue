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
        <label for="">Tekst</label>
        <input v-model="textDa" type="url" placeholder="url tekst">
        <div class="checkboxContainer">
            <label for="">åben i ny fane</label>
            <select name="" id="" v-model="typeEn">
            <option v-for="(type, index) in types" :Key="index" :value="type">{{type}}</option>
            </select>
        </div>
      </div>
      <div v-show="showEn == true" class="editorWrapper">
        <label for="">Tekst</label>
        <input v-model="textEn" type="text" placeholder="url tekst">
        <div class="checkboxContainer">
            <label for="">åben i ny fane</label>
            <select name="" id="" v-model="typeEn">
            <option v-for="(type, index) in types" :Key="index" :value="type">{{type}}</option>
            </select>
        </div>
      </div>
      </div>
      <p>preview</p>
      <div class="preview" v-show="showDa == true" >
        
      </div>
      <div class="preview" v-show="showEn == true">
        
      </div>
    </div>
  </template>
  
  <script>
  export default {
  data(){
      return{
          types:[
            'h1',
            'h2',
            'h3',
            'h4',
            'h5',
            'h6',
            'p'
          ],
          textDa:'',
          typeDa:'',
          textEn:'',
          typeEn:'',
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