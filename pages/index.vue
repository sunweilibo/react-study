<template>
  <div class="diary-login-wrapper">
    <div class="diary-login">
      <div class="outside-wrapper">
        <p class="header-title">
          Welcome to my diary App
        </p>
        <el-form v-if="isLogin" class="login-form" label-width="80px">
          <el-form-item label="登录名">
            <el-input v-model="userName"></el-input>
          </el-form-item>
          <el-form-item label="密码">
            <el-input v-model="userPassword" type="password">
            </el-input>
          </el-form-item>
          <el-form-item>
            没有账号?
            <span
              class="register-link"
              @click="isLogin=false">
              点击注册
            </span>
          </el-form-item>
          <el-form-item>
            <el-button type="primary">
              登录
            </el-button>
          </el-form-item>
        </el-form>
        <el-form v-else class="login-form" label-width="80px">
          <el-form-item label="登录名">
            <el-input v-model="userName"></el-input>
          </el-form-item>
          <el-form-item label="密码">
            <el-input
              v-model="userPassword"
              type="password">
            </el-input>
          </el-form-item>
          <el-form-item label="确认密码">
            <el-input
              v-model="userRepeatPassword"
              type="password">
            </el-input>
          </el-form-item>
          <el-form-item>
            点击
            <span
              class="register-link"
              @click="isLogin=true">
              返回登录
            </span>
          </el-form-item>
          <el-form-item>
            <el-button @click="isLogin=false">
              注册
            </el-button>
          </el-form-item>
        </el-form>
      </div>
    </div>
  </div>
</template>

<script>
export default{
  data() {
    return {
      userName: '',
      userPassword: '',
      isLogin: true
    };
  }
};
</script>

<style lang="scss" scoped>
.diary-login-wrapper{
  width: 100%;
  height: 100vh;
  margin: 0 auto;
  background-color: grey;
  .diary-login{
    position: relative;
    width: 100%;
    height: 100%;
    background-repeat: no-repeat;
    background-size: 100% 100%;
    background-image: url('../assets/img/login.jpeg');
    .outside-wrapper{
      position: absolute;
      top: 50%;
      left: 150px;;
      transform: translateY(-50%);
      .header-title{
        color: #ffffff;
        font-size: 50px;
        margin-bottom: 80px;
      }
      .login-form{
        margin-left: 90px;
        left: 400px;
        height:300px;
        width: 300px;
        .register-link{
          color: #b8e6c3;
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
    }
  }
}
</style>
