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
          resaultDa:'',
          linkEn:'',
          linkTextEn:'',
          fanEn:false,
          resaultEn:'',
          showDa:true,
          showEn:false
      }
  },
  watch:{
    resaultDa(newText, oldText){
          if(newText != oldText){
              this.$emit('sendLinkDa', this.resaultDa)
              console.log('sent')
          }
      },
      resaultEn(newText, oldText){
          if(newText != oldText){
              this.$emit('sendLinkEn', this.resaultEn)
              console.log('sent')
          }
      },
      //create da a tag
      linkTextDa(newData, oldData){
        if(newData != oldData){
          this.resaultDa = `<a href="${this.linkDa}" :target="${this.fanDa == true ? '_blank' : ''}">${this.linkTextDa}</a>`
        }
      },
      linkDa(newData, oldData){
        if(newData != oldData){
          this.resaultDa = `<a href="${this.linkDa}" :target="${this.fanDa == true ? '_blank' : ''}">${this.linkTextDa}</a>`
        }
      },
      fanDa(newData, oldData){
        if(newData != oldData){
          this.resaultDa = `<a href="${this.linkDa}" :target="${this.fanDa == true ? '_blank' : ''}">${this.linkTextDa}</a>`
        }
      },
      //create eng a tag
      linkTextEn(newData, oldData){
        if(newData != oldData){
          this.resaultEn = `<a href="${this.linkEn}" :target="${this.fanEn == true ? '_blank' : ''}">${this.linkTextEn}</a>`
        }
      },
      linkEn(newData, oldData){
        if(newData != oldData){
          this.resaultEn = `<a href="${this.linkEn}" :target="${this.fanEn == true ? '_blank' : ''}">${this.linkTextEn}</a>`
        }
      },
      fanEn(newData, oldData){
        if(newData != oldData){
          this.resaultDa = `<a href="${this.linkEn}" :target="${this.fanEn == true ? '_blank' : ''}">${this.linkTextEn}</a>`
        }
      }

  },
  methods:{

    }
  }
  </script>
  
  <style lang="scss" scoped>
  @import "../../../assets/styles/editorStyles.scss";
  </style>