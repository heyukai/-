<template>
  <div id="building">
  <div class="register-container">
    <div style="text-align: center;height: 50px">
      注册
    </div>
    <el-form :model="registerData" label-width="80px">
      <el-form-item label="用户名">
        <el-input v-model="registerData.username" placeholder="请输入用户名"></el-input>
      </el-form-item>
      <el-form-item label="密码">
        <el-input type="password" v-model="registerData.password" placeholder="请输入密码"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="register" style="margin-left: 100px;width: 70px">注册</el-button>
      </el-form-item>
    </el-form>
  </div>
  </div>
</template>

<script>
import { ElForm, ElFormItem, ElInput, ElButton } from 'element-plus';

export default {
  name: 'RegisterPage',
  components: {
    ElForm,
    ElFormItem,
    ElInput,
    ElButton,
  },
  data() {
    return {
      registerData: {
        username: '',
        password: '',
      },
    };
  },
  methods: {
    register() {
      if (this.registerData.username === '' || this.registerData.password === '') {
        // 用户名或密码为空
        this.$message.error('用户名或密码不能为空');
        return;
      }
      this.$router.push('/login');
      // 执行注册逻辑
      // ...
    },
  },
};
</script>

<style scoped>
.register-container {
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
