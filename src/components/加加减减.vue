<template>
  <div id="app">
    <ul>
      <li v-for="(item, index) in arr" :key="item">
        <span>{{ item }}</span>
        <button @click="del(index)">删除</button>
      </li>
    </ul>
    <button @click="add">生成</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      arr: [1, 5, 3],
    };
  },
  methods: {
    add() {
      this.arr.push(Math.floor(Math.random() * 10000));
    },
    del(id) {
      this.arr.splice(id, 1);
    },
  },
};
</script>