<!--
 * @Author: your name
 * @Date: 2019-11-07 15:48:56
 * @LastEditTime: 2019-11-15 15:22:21
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \app\src\components\banner.vue
 -->
<template>
   <div>
     <span v-for="(item,index) in tits" :key="index" @touchstart="changecolor(index)"  v-bind:class="{list :item.isCompletes}">{{item.tit}}</span>
     <hr>
   </div>
</template>
<script>
export default {
  name: '',
  data () {
    return { 
       tits:[
         {
           tit:"点餐",
           isCompletes:true
         },
          {
           tit:"评价",
            isCompletes:false
         },
          {
           tit:"商家",
            isCompletes:false
         }
       ],
    }
  },
  components:{
  },
  methods:{
        changecolor(i){
          // console.log(i)
          for(let index in this.tits){
             this.tits[index].isCompletes = false;
          }
          this.tits[i].isCompletes =  true;
        }
    } 
}
</script>
<style scoped>
div{
   margin: 20px 30px;
  text-align: center;
}
span{
  font-size: .2rem;
  margin-left: 20px;
}
.list{
  font-size: .2rem;
  margin-left: 20px;
  background:url(../assets/img/di3.png) no-repeat;
  background-position:0 24px;
}
</style>
