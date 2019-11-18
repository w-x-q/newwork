<!--
 * @Author: 熊小兜
 * @Date: 2019-11-07 00:23:30
 * @LastEditors: Please set LastEditors
 * @LastEditTime: 2019-11-15 21:52:20
 * @Description:"搜索"
 -->
<template>
    <div class="box">
        <input type="text" :placeholder="tetil" v-model="name">
        <img class="searchimg" src="../assets/img/search.png" alt="" @click ="loginCheck">
    </div>
</template>
<script>
export default {
    name:"Search",
    data(){
        return {
            tetil:"请输入店名或美食名",
            arr:[],
            name:''
        }
        
    },
    methods:{
    
    loginCheck(){
			 fetch('/api/shops/name?name='+this.name,{
                method:"get"
            })
            .then(res=>{
                return res.json();
            })
            .then(data=>{

            this.arr = data.rows;
            console.log(".........")
            console.log(this.arr.length)
            console.log(data)
            if(this.arr.length==0 || this.arr.length ==6){
                return;
            }else{
                setTimeout(()=>{
                    let arrs=this.arr;
                    console.log(arrs)
						let str = "/titlepage"+arrs;
						this.$router.push( {path:str});
                    },1000);
                //this.tiao(arr)
                    
            }
            console.log("---------");
            console.log( data)
            })
            .catch(err=>{
                    console.log(err);
                })
            },
         tiao(mallCode){
        this.$router.push({
          path: '/titlepage',
          // name: 'mallList',
          query: {
            mallCode: this.arr,
          }
        })
      }
            
    
    }
}
    
</script>
<style scoped>
.box{
    position: relative;
    width: 100%;
    height: .5rem;
    background-color: rgb(37, 157, 238);
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 5px;
}
.searchimg{
    position: absolute;
    left: 10px;
    top: .1rem;
    width: .3rem;
    height: .3rem;

}
input{
    width: 80%;
    height: .3rem;
    border-radius: 10px;
    margin-left: 0.3rem;
    padding-left: 0.1rem;
    outline: 0;     /*掉input的外边框*/
    font-size: 0.1rem;
}
</style>