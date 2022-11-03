<template>
    <div class="inputEditor">
      <div class="editorContainer inputEditorContainer linkEditorContainer">
      <div class="editorWrapper">
        <label for="">Link</label>
        <input v-model="link" type="url" placeholder="url">
        <input v-model="linkText" type="url" placeholder="url tekst">
        <div class="checkboxContainer">
            <label for="">åben i ny fane</label>
            <input type="checkbox" @click="fan = !fan">
        </div>
      </div>
      </div>
      <p>preview</p>
      <div class="preview">
        <a :href="link" :target="fan == true ? '_blank' : ''">{{linkText}}</a>
      </div>
    </div>
  </template>
  
  <script>
  export default {
  data(){
      return{
          link:'',
          linkText:'',
          fan:false,
          resault:'',

      }
  },
  watch:{
    resault(newText, oldText){
          if(newText != oldText){
              this.$emit('sendLink', this.resault)
              console.log('sent')
          }
      },
      //creating the a tag
      linkText(newData, oldData){
        if(newData != oldData){
          this.resault = `<a href="${this.link}" :target="${this.fan == true ? '_blank' : ''}">${this.linkText}</a>`
        }
      },
      link(newData, oldData){
        if(newData != oldData){
          this.resault = `<a href="${this.link}" :target="${this.fan == true ? '_blank' : ''}">${this.linkText}</a>`
        }
      },
      fan(newData, oldData){
        if(newData != oldData){
          this.resault = `<a href="${this.link}" :target="${this.fan == true ? '_blank' : ''}">${this.linkText}</a>`
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