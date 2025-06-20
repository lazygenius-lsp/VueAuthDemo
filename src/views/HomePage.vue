<template>
  <div>
    <h1>欢迎回来，{{ user.name }}！</h1>
    <p>您的邮箱是：{{ user.email }}</p>
    <router-link to="/login">退出登录</router-link>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: { name: '', email: '' }
    };
  },
  mounted() {
    const saved = localStorage.getItem('user');
    this.user = saved ? JSON.parse(saved) : { name: '访客', email: '无' };
  }
};
</script>
