<template>
  <form @submit.prevent="handleLogin">
    <input v-model="name" placeholder="用户名" />

    <input
      v-model="email"
      type="email"
      placeholder="邮箱"
      @blur="validateEmail"
    />
    <p v-if="emailError" style="color: red;">{{ emailError }}</p>

    <button :disabled="!name || !email || !!emailError">登录</button>
  </form>
</template>

<script>
export default {
  name: 'LoginForm',
  data() {
    return {
      name: '',
      email: '',
      emailError: ''
    };
  },
  methods: {
    validateEmail() {
      const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      if (!this.form.email) {
        this.emailError = '邮箱不能为空';
      } else if (!emailPattern.test(this.form.email)) {
        this.emailError = '邮箱格式不正确';
      } else {
        this.emailError = '';
      }
    },
    handleLogin() {
      this.validateEmail();
      if (this.emailError) return;

      const storedUser = JSON.parse(localStorage.getItem('user'));
      if (storedUser && storedUser.name === this.name && storedUser.email === this.email) {
        alert('登录成功');
        this.$emit('login-success');
      } else {
        alert('用户名或邮箱不匹配');
      }
    }
  }
};
</script>
