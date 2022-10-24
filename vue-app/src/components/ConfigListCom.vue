<template>
  <div>
    <div class="listInfo">
    <div class="col-6">
        <p>Navn</p>
        <p>Type</p>
        <p>Sidst opdateret</p>
    </div>
    <div>
        <p>Level</p>
        <p>Rediger</p>
    </div>
    </div>
    <ul class="pageList" v-for="item in listData" :key="item.pageId">
        <li class="" v-if="item.pageId == 1">
            <div class="listItem">
                <div class="listItem__info col-6">
                    <p>{{item.pageName}}</p>
                    <p>{{item.filename}}</p>
                    <p>{{item.updated}}</p>
                </div>
                <div class="listItem__edit col-6">
                    <p>{{item.pageId}}</p>
                    <button><i class="fa-solid fa-pen"></i></button>
                </div>
            </div>
        </li>
            <ul>
                <li v-if="item.pageId == 2">
                    <div class="listItem subItem">
                        <div class="listItem__info col-6">
                            <p>{{item.pageName}}</p>
                            <p>{{item.filename}}</p>
                            <p>{{item.updated}}</p>
                        </div>
                        <div class="listItem__edit col-6">
                            <p>{{item.pageId}}</p>
                            <button><i class="fa-solid fa-pen"></i></button>
                        </div>
                    </div>
                </li>
                <ul v-if="item.pageId == 3">
                    <li>
                        <div class="listItem subItem">
                            <div class="listItem__info col-6">
                                <p>{{item.pageName}}</p>
                                <p>{{item.filename}}</p>
                                <p>{{item.updated}}</p>
                            </div>
                            <div class="listItem__edit col-6">
                                <p>{{item.pageId}}</p>
                                <button><i class="fa-solid fa-pen"></i></button>
                            </div>
                        </div>
                    </li>
                </ul>
            </ul>

    </ul>
  </div>
</template>

<script>
import axios from 'axios'
export default {
name:"ConfigListCom",
data(){
    return{
        listData:[]
    }
},
mounted(){
    this.getListData()
},
methods:{
   async getListData(){
    try{
    axios.get('http://dev-api.guestbox.dk/cms/pages/1').then((response)=>{
        response.data.sort((a,b) => (a.pageId - b.pageId))
        this.listData = response.data
    })

    }catch(error){
        console.log(error)
    }
    }
}
}
</script>

<style lang="scss" scoped>
.listInfo{
    display: flex;
    justify-content: space-between;
    div{
        justify-content: space-between;
        display: flex;  
        padding-left: 40px;
    }
    div:nth-child(2){
        gap:8px
    }
}
ul{
    margin:0
}
li{
    list-style-type:none
}
.pageList{
    padding-left: 0;
}
.listItem{
    border:solid black 2px;
    display: flex;
    justify-content: space-between;
&__info{
    display: flex;
    justify-content: space-between;
    &:nth-child(1){
        padding-left: 40px;
    }
}
&__edit{
    display: flex;
    justify-content: flex-end;
    gap:28px;
    align-items: center;
    p{
        margin:0;
    }
    button{
        background: none;
        border:none;
        outline:none;
        padding:none;
        height: fit-content;
        i{
            background-color: black;
            color:white;
            padding:6px;
            border-radius: 8px;
            
        }
    }
}
}
.subItem{
    border-top: none;
}
</style>