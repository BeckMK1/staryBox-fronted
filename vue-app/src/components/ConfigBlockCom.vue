<template>
  <div>
    <transition>
    <div v-if="isEdit == false">
    <div class="listInfo">
        <div class="col-6">
            <p>Navn</p>
            <p>Type</p>
            <p>Sidst opdateret</p>
        </div>
        <div>
            <p>Rediger</p>
        </div>
    </div>
    <div v-if="isLoading == true" class="loader"></div>
    <ul class="pageList" v-for="(items, index) in chunkList" :key="index" v-show="index == this.currentPage">
        <li v-for="item in items" :key="item.blockId" class="listItem"  >
            <div class="listItem__info col-6">
                <p>{{item.blockName}}</p>
                <p>{{item.blockType}}</p>
                <p>{{item.folderId}}</p>
            </div>
            <div class="listItem__edit col-6">
                <button @click="isEdit = true"><i class="fa-solid fa-pen"></i></button>
            </div>
        </li>
    </ul>
    <div class="listNav">
        <button @click="goLeft()"><i class="fa-solid fa-arrow-left"></i></button>
        <span :class="currentPage == index ? 'selectedPage' : '' " v-for="(items, index) in chunkList" :key="index" @click="currentPage = index">{{index + 1}}</span>
        <button @click="goRight()"><i class="fa-solid fa-arrow-right"></i></button>
    </div>
  </div>
</transition>
<config-editor-com v-if="isEdit == true"></config-editor-com>
</div>

</template>

<script>
import axios from 'axios'
import ConfigEditorCom from './ConfigEditorCom.vue'
export default {
  components: { ConfigEditorCom },
    name:"ConfigBlockCom",
    data(){
        return{
            listData:null,
            chunkList:[],
            currentPage:0,
            isLoading:true,
            isEdit:false
        }
    },
    props:{
        showBlock:Number
    },
mounted(){
    this.getListData()
},  
methods:{
splitChunk() {
    const chunksize = 3
    for (let start=0; start < this.listData.length; start += chunksize) {
        let tempData;
        tempData = this.listData.slice(start, start + chunksize);
        this.chunkList.push(tempData)
    }
},
goLeft(){
    if(this.currentPage != 0){
        this.currentPage--
    }
},
goRight(){
    if(this.currentPage != this.chunkList.length -1){
    this.currentPage++
}
},
async getListData(){
    try{
    axios.get('http://dev-api.guestbox.dk/cms/blocks/1').then((response)=>{
        response.data.sort((a,b) => (a.pageId - b.pageId))
        this.listData = response.data
        this.splitChunk()
        this.isLoading = false
    })
    }catch(error){
        console.log(error)
    }
    }
},
}
</script>

<style lang="scss" scoped>
@import "../assets/styles/configList.scss";
.pageList{
    min-height: 132px;
}
.listInfo{
    padding-left: 0;
    div:first-child{
        position: relative;
        p:nth-child(2){
            position: absolute;
            right: 41%;
        }
        p:nth-child(3){
            position: absolute;
            right: 0%;
        }
    }
}
.listItem{
    border-top: none;
}
.listItem:nth-child(1){
        border-top:solid black 2px;
    }

.listNav{
    margin-top: 8px;
    span{
        cursor: pointer;
        user-select: none;
        padding: 4px 8px;
        border-radius: 50%;
        transition: 200ms ease;
    }
    span:hover{
        background-color: black;
        color: white;
    border-radius: 50%;
    transition: 200ms ease;
    }
    button{
        margin: 0 8px;
        background-color: black;
        color: white;
        border: transparent solid 1px;
        border-radius: 50%;
    border-radius: 50%; 
    padding: 4px 8px;
    transition: 200ms ease;
    &:hover{
        background-color: white;
        color: black;
        border-color: black;
        border-radius: 50%;
        transition: 200ms ease;
    }
    }
}

.selectedPage{
    background: black;
    padding: 4px 8px;
    color: white;
    border-radius: 50%;
}
</style>