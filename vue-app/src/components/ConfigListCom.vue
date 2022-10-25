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
    <ul class="pageList">
        <div v-for="item in listData" :key="item.pageId">
        <li class="" v-if="item.pageId == 1">
            <div class="listItem">
                <div class="listItem__info col-6">
                    <p>{{item.linkname}}</p>
                    <p>{{item.filename}}</p>
                    <p>{{item.updated}}</p>
                </div>
                <div class="listItem__edit col-6">
                    <p>{{item.pageId}}</p>
                    <button @click="$emit('goToEdit', item.pageId)"><i class="fa-solid fa-pen"></i></button>
                </div>
            </div>
        </li>
            <ul>
                <li v-if="item.pageId == 2">
                    <div class="listItem subItem">
                        <div class="listItem__info col-6">
                            <p>{{item.linkname}}</p>
                            <p>{{item.filename}}</p>
                            <p>{{item.updated}}</p>
                        </div>
                        <div class="listItem__edit col-6">
                            <p>{{item.pageId}}</p>
                            <button @click="$emit('goToEdit', item.pageId)"><i class="fa-solid fa-pen"></i></button>
                        </div>
                    </div>
                </li>
                <ul v-if="item.pageId == 3">
                    <li>
                        <div class="listItem subItem">
                            <div class="listItem__info col-6">
                                <p>{{item.linkname}}</p>
                                <p>{{item.filename}}</p>
                                <p>{{item.updated}}</p>
                            </div>
                            <div class="listItem__edit col-6">
                                <p>{{item.pageId}}</p>
                                <button @click="$emit('goToEdit', item.pageId)"><i class="fa-solid fa-pen"></i></button>
                            </div>
                        </div>
                    </li>
                </ul>
            </ul>
        </div>
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
},
}
</script>

<style lang="scss" scoped>
@import "../assets/styles/configList.scss";
</style>