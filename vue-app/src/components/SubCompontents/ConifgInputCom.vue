<template>
      <div class="metaInput">
          <div v-if="dropdown == false">
              <label :for="name">{{label}}</label>
              <input :name="name" :type="type" v-model="inputData" :style="inputSize">
          </div>
          <div v-if="dropdown == true">
              <label :for="name">{{label}}</label>
              <select :name="name" v-model="inputData">
              <option v-for="(option, index) in options" :key="index">{{option}}</option>
              </select>
          </div>
      </div>
  </template>
  
  <script>
  export default {
  name:"ConfigInputCom",
  props:{
  label:String,
  type:String,
  name:String,
  dropdown:{
    type:Boolean,
    default:false
  },
  size:{
    type:String,
    default:"100px"
  },
  options:Array
  },
  data(){
    return{
        inputData:"",
        inputSize:"width:" + this.size
    }
  },
  watch:{
    inputData(newData, oldData){
        if(newData != oldData){
            this.$emit("sendInput", this.inputData)
        }
    }
  }
  }
  </script>
  
  <style lang="scss" scoped>
  .metaInput{
    width: fit-content;
    label{
        width: 100%;
        text-align: start;
        font-weight: bold;
    }
    input{
        display: block;
    }
    select{
        display: block;
    }
  }
  </style>