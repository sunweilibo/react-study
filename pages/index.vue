<template>
  <div class="diary-login-wrapper">
    <div class="diary-login">
      <div class="outside-wrapper">
        <p class="header-title">
          Welcome to my diary App
        </p>
        <login v-if="isLogin" @goRegister="goRegister"></login>
        <register v-else @goLogin="goLogin"></register>
      </div>
    </div>
  </div>
</template>

<script>
import login from '~/components/log/login.vue';
import register from '~/components/log/register.vue';
export default {
  components: { login, register },
  data() {
    return {
      isLogin: true
    };
  },
  methods: {
    goRegister() {
      this.isLogin = false;
    },
    goLogin() {
      this.isLogin = true;
    }
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
        margin-bottom: 40px;
      }
    }
  }
}
</style>
