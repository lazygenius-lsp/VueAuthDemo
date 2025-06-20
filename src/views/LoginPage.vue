<template>
  <div>
    <h1>登录页面</h1>
    <LoginForm @login-success="goToHome" />
    <p>还没有账号？<router-link to="/register">去注册</router-link></p>
  </div>
</template>

<script>
import LoginForm from '../components/LoginForm.vue';

export default {
  components: { LoginForm },
  methods: {
    goToHome() {
      this.$router.push('/home');
    }
  }
};
</script>
