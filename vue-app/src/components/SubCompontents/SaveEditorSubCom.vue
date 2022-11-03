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
  data(){
    return{
        save:true
    }
  },
  methods:{
      sendSave(){
          this.$emit('sendSave', this.save)
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
      background-color: rgb(204, 202, 202);
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
          margin-right: 30px;
      }
  }
  </style>