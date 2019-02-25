<template>
  <div>
    <el-form
      ref="registerForm"
      :model="registerParams" class="login-form"
      label-width="80px" :rules="rules">
      <el-form-item label="登录名" required prop="registerName">
        <el-input v-model="registerParams.registerName"></el-input>
      </el-form-item>
      <el-form-item label="密码" required prop="newPassword">
        <el-input v-model="registerParams.newPassword" type="password">
        </el-input>
      </el-form-item>
      <el-form-item label="确认密码" required prop="repeatPassword">
        <el-input v-model="registerParams.repeatPassword" type="password">
        </el-input>
      </el-form-item>
      <el-form-item>
        点击
        <span class="register-link" @click="goLogin">
          返回登录
        </span>
      </el-form-item>
      <el-form-item>
        <el-button @click="register">
          注册
        </el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default{
  data() {
    var checkRepeat = (rule, value, callback) => {
      if (this.registerParams.newPassword !== value) {
        callback(new Error('两次密码输入不一致'));
      } else {
        callback();
      }
    };
    return {
      registerParams: {
        registerName: '',
        newPassword: '',
        repeatPassword: ''
      },
      rules: {
        registerName: [
          { required: true, message: '请输入注册账号名称', trigger: 'blur' },
          { min: 6, max: 20, message: '长度在6到20个字符', trigger: 'blur' }
        ],
        newPassword: [
          { required: true, message: '请输6到20位密码', trigger: 'blur' },
          { min: 6, max: 20, message: '长度为6到20个字符', trigger: 'blur' }
        ],
        repeatPassword: [
          { validator: checkRepeat, trigger: 'blur' }
        ]
      }
    };
  },
  methods: {
    goLogin() {
      this.$emit('goLogin');
    },
    register() {
      this.$refs.registerForm.validate((valid) => {
        if (valid) {
          alert('submit!');
        } else {
          console.log('error submit!!');
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
