<template>
    <div class="saveContainer">
      <div class="save" @click="sendSave">
          <span>Gem</span>
      </div>
    </div>
  </template>
  
  <script>
  export default {
  name:'SaveEditorSubC',
  methods:{
      sendSave(){
          this.$emit('sendSave')
      }
  }
  }
  </script>
  
  <style lang="scss" scoped>
  .saveContainer{
      position: fixed;
      bottom: 0;
      width: 100vw;
      height: 50px;
      background-color: rgba($color: black, $alpha: 0.3);
      display: flex;
      justify-content: flex-end;
      align-items: center;
      left: 0px;
  
      .save{
          padding: 8px;
          color: white;
          font-weight: bold;
          background-color: black;
          width: fit-content;
          margin-right: 8px;
      }
  }
  </style>