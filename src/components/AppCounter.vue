<template>
  <div class="counter">
    <h2>{{ title }}</h2>
    <p>当前计数：{{ count }}</p>
    <button @click="increment">+1</button>
    <button @click="reset">重置</button>
  </div>
</template>

<script>
export default {
  name: 'AppCounter',
  props: {
    title: {
      type: String,
      default: '计数器'
    }
  },
  data() {
    return {
      count: 0
    };
  },
  methods: {
    increment() {
      this.count++;
    },
    reset() {
      this.count = 0;
    }
  }
};
</script>

<style scoped>
.counter {
  padding: 1rem;
  border: 1px solid #ccc;
  border-radius: 8px;
  max-width: 300px;
}
button {
  margin-right: 8px;
}
</style>
