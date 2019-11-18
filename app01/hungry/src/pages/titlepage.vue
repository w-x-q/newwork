<!--
 * @Descripttion: "首页"
 * @version: v1.0.0
 * @Date: 2019-11-06 14:35:10
 * @LastEditors: Please set LastEditors
 * @LastEditTime: 2019-11-15 22:09:42
 -->
<template>
  <div class="box">
      <Search style="position:fixed;z-index:2;"></Search>
      <div class="center">
          <div class="body">
              <ul>
                  <li v-for="(item,index) in arr" :key="index">
                      {{item.shopname}}
                  </li>
              </ul>
          </div>
      </div>
      <Footer  style="position:fixed;z-index:2;bottom:0px;"></Footer>
  </div>
</template>

<script>
import Search from '../components/Search';

import Footer from '../components/Footer';

export default {
  name: 'page',
  props:['arr'],
  data () {
    return {
      arr:[]
    }
  },
  components:{
     Search,Footer
  },
  methods:{
      getParams(){
        // 取到路由带过来的参数
        const routerParams = this.$route.query.mallCode;
        // 将数据放在当前组件的数据内
        this.arr = routerParams;
        console.log(routerParams)
      },
  }
}
</script>

<style scoped>
.box{
  display: flex;
  flex-direction: column;
  height: 100%;  
}
.center{
    flex: 1;
    overflow-y: auto;
    /* margin-top: .6rem; */
}
.body{
    width: 100%;
    height: 5rem;
    background-color: rgb(147, 187, 247);
}
</style>
