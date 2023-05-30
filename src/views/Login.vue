<template>
  <div id="building">
  <div class="login-container">
    <div style="text-align: center;height: 50px">
      登录
    </div>
    <el-form :model="loginData" label-width="80px">
      <el-form-item label="用户名">
        <el-input v-model="loginData.username" placeholder="请输入用户名"></el-input>
      </el-form-item>
      <el-form-item label="密码">
        <el-input type="password" v-model="loginData.password" placeholder="请输入密码"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="login" class="loginbutton">登录</el-button>
      </el-form-item>
       <p class="register-link" @click="goToRegister" style="text-align: center;height: 50px">没有账号？点击注册</p>
    </el-form>
  </div>
  </div>
</template>

<script>
import { ElForm, ElFormItem, ElInput, ElButton } from 'element-plus';

export default {
  name: 'LoginPage',
  components: {
    ElForm,
    ElFormItem,
    ElInput,
    ElButton,
  },
  data() {
    return {
      loginData: {
        username: '',
        password: '',
      },
    };
  },
  methods: {
    login() {
      if (this.loginData.username === '' || this.loginData.password === '') {
        // 用户名或密码为空
        this.$message.error('用户名或密码不能为空');
        return;
      }
      let userData = {
                        username: this.loginData.username, //账号
                        password: this.loginData.password,
                        head: '../assets/'+this.loginData.username+'.jpg', 
                    };
                    sessionStorage.setItem("userData", JSON.stringify(userData))
      this.$router.push('/home');
      // 执行登录逻辑
      // ...
    },
    goToRegister() {
      this.$router.push('/register');
    },
  },
};
</script>

<style scoped>
.login-container {
  width: 400px;
  height: 250px;
  background: #e5e9f2;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  border-radius: 5px;
  padding-top: 40px;
  padding-right: 40px;
}
#building{
  background:url("../assets/BJ1.jpg");
  width:100%;
  height:100%;
  position:fixed;
  background-size:100% 100%;}

</style>
