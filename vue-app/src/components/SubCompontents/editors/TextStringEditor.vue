<template>
    <div class="inputEditor">
      <div class="editorContainer inputEditorContainer linkEditorContainer">
      <div class="editorWrapper">
        <label for="">Tekst</label>
        <input v-model="text" type="url" placeholder="url tekst">
        <div class="checkboxContainer">
            <label for="">åben i ny fane</label>
            <select name="" id="" v-model="type">
            <option v-for="(type, index) in types" :Key="index" :value="type">{{type}}</option>
            </select>
        </div>
      </div>
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
          text:'',
          type:'',
          resault:'',
      }
  },
  watch:{
    resault(newText, oldText){
          if(newText != oldText){
              this.$emit('sendTextString', this.resault)
              console.log('sent')
          }
      },
      type(newData, oldData){
        if(newData != oldData){
          this.resault = `<${this.type}>${this.text}</${this.type}>`
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