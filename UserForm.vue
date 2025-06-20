<template>
  <div class="form-wrapper">
    <h2>用户信息表单</h2>

    <form @submit.prevent="handleSubmit">
      <div class="form-group">
        <label for="name">用户名：</label>
        <input id="name" v-model="form.name" type="text" placeholder="请输入用户名" />
      </div>

      <div class="form-group">
        <label for="email">邮箱：</label>
        <input
          id="email"
          v-model="form.email"
          type="email"
          placeholder="请输入邮箱"
          @blur="validateEmail"
        />
        <p v-if="emailError" style="color: red;">{{ emailError }}</p>
      </div>

      <button type="submit" :disabled="!form.name || !form.email || !!emailError">提交</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'UserForm',
  data() {
    return {
      form: {
        name: '',
        email: ''
      },
      emailError: ''
    };
  },
  methods: {
    validateEmail() {
      const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      if (!emailPattern.test(this.form.email)) {
        this.emailError = '请输入有效的邮箱地址';
      } else {
        this.emailError = '';
      }
    },
    handleSubmit() {
      this.validateEmail();
      if (this.emailError) return;

      localStorage.setItem('user', JSON.stringify(this.form));
      alert('注册成功！');
      this.$emit('register-success');
    }
  }
};
</script>
