<!--
 * @Author: 熊小兜
 * @Date: 2019-11-11 09:25:52
 * @LastEditors: Please set LastEditors
 * @LastEditTime: 2019-11-15 17:18:27
 * @Description: 
 -->
<template>
    <div>
        <div class="header">
           <img src="../assets/img/logo.png" class="image">
        </div>
        <div class="input-group">
            <input type="text" class="form-control" placeholder="电话号码" v-model="name">
			
        </div>
        <div class="input-group">
            <input type="text" class="form-control" placeholder="密码" aria-describedby="basic-addon1" v-model="password">
        </div>
        <div class="input-group">
            <input type="text" class="form-control" placeholder="确认密码" aria-describedby="basic-addon1">
        </div>
        <div class="input-group">
            <input type="button" value="注册" class="ZC"  @click="registerCheck" >
        </div>
        <p class="reg">  <router-link to="/Loginpage">已有账号请登录</router-link></p>
    </div>
</template>
<script>
import { Toast } from 'mint-ui'; 
export default {
     name: 'Register',
  	data () {
    	return {
		name:'',
		password:''
    	}
	  }
	  ,
	  methods: {
		   registerCheck(){
			   let username="";
			   let pass="";
			   let n=this.name+'';
			   let p=this.password+'';
			 fetch('/api/user/register?username='+n+'&'+"pass="+p,{
                method:"post"
            })
            .then(res=>{
                return res.json();
            })
            .then(data=>{
				 console.log(data)
                if(data.success == true){
    
                    // alert("注册成功")
					setTimeout(()=>{
						let str = "/LoginPage";
						this.$router.push({path:str});
					},1100);

					// this.$router.push({path:"/RegisterTwo/"+mg});
						}else{
							alert("亲：验证码过期")
						}
					})	
					.catch(err=>{
						console.log(err);
					})
			}
 	 }
}
</script>
<style scoped>
.box{
	width: 4rem;
	height: 4.5rem;
}
.header{
	width: 100%;
	height:1rem;	
	padding-top: 0.3rem;
	margin-bottom: 0.3rem;
}
.image{
	width: 2rem;
	height: 0.7rem;
	margin: 0 0.75rem;	
}
.input-group{
	width: 3rem;
	margin-left: .45rem;
	margin-top: 0.2rem;
}
.form-control{
	outline: none;
	width: 2.5rem;
	height: 0.3rem;
	border-radius: 5px;
}
.control{
	margin-top: 10px;
	outline: none;
	width: 1.5rem;
	height: 0.3rem;
	border-radius: 5px;
}
.ZC{
	width: 2.5rem;
	height: 0.45rem;
	background: rgb(49, 144, 221);
	border: none;
	border-radius: 0.15rem;	
	margin-top: 0.2rem;	
	color: white;
	font-size:0.2rem;
}
.reg{
	margin-top: .2rem;
	margin-left: .25rem;
}
</style>