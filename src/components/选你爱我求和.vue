<template>
  <div>
    <h2>选你爱我求和</h2>
    <div v-for="item in arr" :key="item">
      {{ item }}
      <input type="checkbox" v-model="checkNumArr" :value="item" />
    </div>
    <h2>求和:{{ sum }}</h2>
  </div>
</template>

<script>
export default {
  data() {
    return {
      arr: [9, 15, 19, 25, 29, 31, 48, 57, 62, 79, 87],
      checkNumArr: [],
    };
  },
  computed: {
    sum() {
      return this.checkNumArr.reduce((sum, next) => (sum += +next), 0);
    },
  },
};
</script>

<style scoped>
h2 {
  margin: 100px;
}
</style>
