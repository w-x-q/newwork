<!--
 * @Descripttion: "轮播图"
 * @version: v1.0.0
 * @Date: 2019-11-06 14:35:10
 * @LastEditors: Please set LastEditors
 * @LastEditTime: 2019-11-15 19:17:22
 -->
<template>
 <div class="box">   
        <div style="display:none" >{{typeid}}</div>
         <ul>
            <li v-for="(shop,index) in sh" :key="index" >
                <div class="imgBox">
                    <img :src="shop.head" alt="">
                </div>
                <div class="infoBox">
                    <ul>
                        <li class="Name">{{shop.shopname}}</li>
                        <li>月销：{{shop.success}}</li>
                        <li>价格：￥{{shop.delivery}}元</li>
                        <li class="eval">评价：{{shop.evaluate}}</li>
                        <li>距离：{{shop.tallys}}</li>
                    </ul>
                </div>
            </li>
        </ul>
    </div>  
</template>

<script>
import axios from 'axios';

export default {
  name: 'Tshops',
  props:['typeid'],
  data () {
    return {
        allShops:[],
        shops:[],
        sh:[],
        oldtype:[]
    }
  },
  created() {
     //从后端获取数据     
    //  axios.get('/allshops')
     axios.get('/shops/clazz?scid='+this.typeid)
     .then(res=>{ 
         console.log(res.data.rows)
         
        //  this.allShops = res.data.rows;//内部数据，由于没有渲染在组件里，所以，没有触发组件更新
        this. shops=res.data.rows;
        this.sh = this.shops;
        console.log(this.shops)
        //  this.shops = this.getBooksByType(this.allShops);//内部数据，由于渲染到了页面，所以，触发了组件更新
    //  console.log(this.typename);
    //     axios('api/tmall/pro?id='+this.typename)
    //     .then(res=>{
    //         this.allgoodslist = res.data;
    //         this.goodslist = this.allgoodslist;

     })
     .catch(err=>{
         console.log(err);
     });
  },
  beforeUpdate(){
    //  console.log("数据更新了------------：");
    //   this.sh = this.getBooksByType(this.sh);
       if(this.typeid!=this.oldtype){
            this.oldtype = this.typeid;
            console.log('更新了',this.typeid);
            
            axios('/shops/clazz?scid='+this.typeid)
            .then(res=>{
                this.sh = res.data.rows;
            })
            .catch(err=>{
                console.log(err);
            })
        }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.box{
  margin: 0 auto;
  width:95%;
}

.box>ul{
    width: 100%;
}

.box>ul>li{
    margin-top:.1rem;
    width: 100%;
    display: flex;
}

.imgBox{
    width:40%;
    height: 1.5rem;
}

.infoBox{
    width: 60%;
    padding-left:10px;
    border-bottom: 1px solid gray;
}
img{
    width: 100%;
    height: 100%;
    border-radius: .05rem;
}
.Name{
    font-size: 0.24rem;
}
.eval{
    color: red;
}
</style>