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
      <div v-show="showDa == true" class="editorWrapper">
      <label for="">Html</label>
      <div class="htmlEditor">
        <div class="lineNumbers">
        </div>
        <textarea v-model="HtmlDa" class="editor" cols="30" rows="10"></textarea>
      </div>
      </div>
      <div v-show="showEn == true" class="editorWrapper">
      <label for="">Html </label>
      <div class="htmlEditor">
        <div class="lineNumbers">
        </div>
        <textarea v-model="HtmlEn" class="editor" cols="30" rows="10"></textarea>
      </div>
      </div>
      </div>
      <div class="preview">

      </div>
    </div>
  </template>
  
  <script>
  export default {
  data(){
      return{
              HtmlDa:'',
              HtmlEn:'',
          showDa:true,
          showEn:false
      }
  },
  watch:{
    HtmlDa(newText, oldText){
        const previewHtml = document.querySelector(".preview");
          if(newText != oldText){
              this.$emit('sendHtmlDa', this.HtmlDa)
              console.log('sent')
              previewHtml.innerHTML = this.HtmlDa
          }
      },
      HtmlEn(newText, oldText){
          if(newText != oldText){
              this.$emit('sendHtmlEn', this.HtmlEn)
              console.log('sent')
          }
      },

  },
  mounted(){
    this.addLineNumbers()
  },
  methods:{
    addLineNumbers(){
        const editors = document.querySelectorAll('.htmlEditor');
        for(let editor of editors){
            const lineNumbers = editor.querySelector('.lineNumbers');
            const textarea = editor.querySelector('textarea');
            textarea.addEventListener('keyup', event =>{
                const NumberOfLines = event.target.value.split('\n').length

                lineNumbers.innerHTML = Array(NumberOfLines).fill(`<span></span>`).join('')
            })
        }
        

    }
  }
  }
  </script>
  
  <style lang="scss" scoped>
  @import "../../../assets/styles/editorStyles.scss";
  </style>