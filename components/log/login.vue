<template>
  <div>
    <el-form
      ref="loginForm" :model="loginParams"
      class="login-form" label-width="80px"
      :rules="rules">
      <el-form-item label="登录名" prop="userName">
        <el-input v-model="loginParams.userName"></el-input>
      </el-form-item>
      <el-form-item label="密码" prop="userPassword">
        <el-input v-model="loginParams.userPassword" type="password">
        </el-input>
      </el-form-item>
      <el-form-item>
        没有账号?
        <span class="register-link" @click="goRegister">
          点击注册
        </span>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="login">
          登录
        </el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default{
  data() {
    return {
      loginParams: {
        userName: '',
        userPassword: ''
      },
      rules: {
        userName: [
          { required: true, message: '账号不能为空', trigger: 'blur' }
        ],
        userPassword: [
          { required: true, message: '密码不能为空', trigger: 'blur' }
        ]
      }
    };
  },
  methods: {
    goRegister() {
      this.$emit('goRegister');
    },
    login() {
      this.$refs.loginForm.validate(valid => {
        if (valid) {
          alert('success');
        } else {
          return false;
        }
      });
    }
  }
};
</script>

<style lang="scss" scoped>
.login-form{
  margin-left: 90px;
  left: 400px;
  height:300px;
  width: 300px;
  .register-link{
    color: #b8e6c3;
    text-decoration: underline;
    &:hover{
      cursor: pointer;
    }
  }
  /deep/ .el-form-item{
    .el-form-item__label{
      color: #ffffff;
    }
  }
}
</style>
