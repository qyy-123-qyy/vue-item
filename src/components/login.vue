<template>
    <div class="login_container">
        <div class="login_box">
        <h4>欢迎注册</h4>
        <div class="vip">
			<span class="hd">老用户登录 </span>
			<span class="tips">尊敬的用户，欢迎您回来!</span>
			<span class="account" @click="goin">还没有账号，<font color="red">去注册</font></span>
		</div>   

           <!-- 登录注册区域 -->
    <el-form  label-width="0px" class="login_form" :model="loginForm" :rules="loginFormRules" ref="loginFormRef">
        <!-- 用户名 -->
        <el-form-item prop="username">
        <el-input v-model="loginForm.username" placeholder="请输入用户名"></el-input>
        </el-form-item>
        <!-- 密码-->
        <el-form-item prop="password">
        <el-input v-model="loginForm.password" type="password" placeholder="请输入密码"></el-input>
        </el-form-item>
          <!-- 按钮 -->
        <el-form-item class="btn">
        <el-button type="primary">登录</el-button>
         <el-button type="info" @click="resetLoginForm">重置</el-button>
        </el-form-item>       
    </el-form> 
    </div>  
</div>

</template>
<script>
export default {
    data(){
        return{
         //登录表单数据对象
         loginForm:{
             username:"",
             password:""
         },
         //表单验证
         loginFormRules:{
        //用户名
         username:[
           { required: true, message: '请输入用户名', trigger: 'blur' },
           { min:3, max: 10, message: '长度在 6 到 10 个字', trigger: 'blur' }
        //    {patter:'/((^[1-9]\d*)|^0)(\.\d{0,2}){0,1}$/', message: '长度在 6 到 10 个字', trigger: 'blur' }
         ],
        //密码
         password:[
           { required: true, message: '请输入密码', trigger: 'blur' },
           { min:6, max: 10, message: '长度在 6 到 10 个字', trigger: 'blur' }
         ]
        
                       },  
             }
      },
     methods:{
         resetLoginForm(){
            //  console.log(this);
             this.$refs.loginFormRef.resetFields();
         },
         goin(){
             this.$router.push("/regist")
         }
     }



}

</script>
<style scoped>
.login_container{
height: 100%;
background-color:#fbfbfb;
}
.login_box{
    width:600px;
    height: 400px;
    background-color: #fff;
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    margin: auto;
    padding:50px 70px;
}
.login_box h4{
    margin: 0;
    padding:0 20px 30px;
    text-align: center;
    font-size: 26px;
}
.vip{
	border: 1px solid #eee;
	position: relative;
    padding: 20px 10px;
}
 .vip .hd{
	color:#FF4466;
	font-size: 18px;
}
 .vip .tips{
	font-size: 14px;
	color: #666;
	margin-left: 20px;
}
 .account{
	position: absolute;
	right:50px;
    font-size:14px;
    cursor: pointer;
}
.login{
    width: 150px;
    height: 60px;
}

.login_form{
  width:300px;
  box-sizing: border-box;
  margin:60px auto;
}
.btn{
   display: flex;
   justify-content:flex-end;
}
</style>