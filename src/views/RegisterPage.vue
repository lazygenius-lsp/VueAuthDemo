<template>
  <div>
    <h1>注册页面</h1>
    <UserForm @register-success="goToLogin" />
    <p>已有账号？<router-link to="/login">去登录</router-link></p>
  </div>
</template>

<script>
import UserForm from '../components/UserForm.vue';

export default {
  components: { UserForm },
  methods: {
    goToLogin() {
      this.$router.push('/login');
    }
  }
};
</script>
