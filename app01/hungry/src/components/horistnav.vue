<!--
 * @Author: your name
 * @Date: 2019-11-07 15:48:56
 * @LastEditTime: 2019-11-15 15:31:07
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \app\src\components\banner.vue
 -->
<template>
<div>
   <ul id="box">
       <!-- <li v-for="(item,index) in types" :key="index" @click="changetype(item.name,isComplete)" v-bind:class="{dian:isComplete}">{{item.name}}</li> -->
       <li v-for="(item,index) in types" :key="index" @click="changetype(item.name,index)" v-bind:class="{dian:isCompletes[index]}">{{item.name}}</li>
     </ul>
     <horistcar :typename="currtype"></horistcar>
     </div>
</template>
<script>
import horistcar from './horistcar';
export default {
  name: 'horistnav',
  
  data () {
 
    return {   
       types:[
        {
            "id":"002",
            "name":"待付款"
        },
        {
            "id":"003",
            "name":"待使用"
        },
        {
            "id":"004",
            "name":"待评价"
        },
        {
            "id":"005",
            "name":"退款/售后"
        }
    ],
       currtype:"待付款",
       isCompletes:[
           true,false,false,false
       ]
    }
    
  },
  components:{
    horistcar
  } ,
  //  created() {
  //     fetch('/api/types')
  //     .then(res=>{
  //       return res.json();
  //     })
  //     .then(data=>{
  //         this.types = data;
  //         this.currtype = this.types[0].name;
  //    })
  //    .catch(err=>{
  //      console.log(err);
  //    })
  // },
  methods:{
     changetype(typename,i){
          console.log(typename);
          this.currtype = typename;
          // this.isComplete=true;
          for(let index in this.isCompletes){
            this.isCompletes[index]  = false;
          }
          this.isCompletes[i] =  true;
      }
  }
}
</script>
<style scoped>
div{
     width: 100%;
     
   }
   ul{
     width: 100%;
     display:flex;
     justify-content:space-around;
     padding: 3%;
     box-sizing: border-box;
     background: #0099ff;
   }
   li{
     border-radius: .05rem;
     width: 23%;
     line-height: .4rem;
     height: .4rem;
     text-align: center;
     font-size: .15rem;
     color:#fff;
   }
   .dian{
     border-radius: .05rem;
     width: 23%;
     line-height: .4rem;
     height: .4rem;
     text-align: center;
     font-size: .15rem;
     color:#fff;
     background:url(../assets/img/di2.png) no-repeat;
     background-position: bottom;
   }
</style>

