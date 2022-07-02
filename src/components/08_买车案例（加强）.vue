<template>
  <div id="app">
    <table class="tb">
      <tr>
        <th><input type="checkbox" v-model="isAll" />全选</th>
        <th>商品</th>
        <th>单价</th>
        <th>数量</th>
        <th>小记</th>
        <th>操作</th>
      </tr>
      <!-- 循环渲染的元素tr -->
      <tr v-for="item in list" :key="item.id">
        <td><input type="checkbox" v-model="item.c" /></td>
        <td>{{ item.name }}</td>
        <td>￥{{ item.price }}</td>
        <td>
          <span @click="addFn1(item.id)">-</span
          ><input type="text" v-model.number="item.count" /><span
            @click="addFn(item.id)"
            >+</span
          >
        </td>
        <td>￥{{ (item.price * item.count).toFixed(2) }}</td>
        <td><button @click="delFn(index)">删除</button></td>
      </tr>

      <tr v-if="list.length === 0">
        <td colspan="4">没有数据咯~</td>
      </tr>
    </table>
    <br />
    <button @click="delAll">删除选中商品</button>
    <button @click="clearAll">清理购物车</button>
    <br />
    <div style="margin-top: 20px">
      <h2>统计</h2>
      <p>已经选中商品件数{{ num }}</p>
      <p>总价{{ allMoney }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      list: [
        { id: 1, name: '奔驰', price: 10, count: 1, c: false },
        { id: 2, name: '宝马', price: 20, count: 1, c: false },
        { id: 3, name: '奥迪', price: 30, count: 1, c: false },
      ],
    }
  },
  methods: {
    delFn(index) {
      // 删除按钮 - 得到索引, 删除数组里元素
      this.list.splice(index, 1)
    },
    addFn(val) {
      const index = this.list.findIndex((ele) => ele.id == val)
      this.list[index].count++
    },
    addFn1(val) {
      const index = this.list.findIndex((ele) => ele.id == val)
      this.list[index].count >= 1 ? this.list[index].count-- : 1
    },
    delAll() {
      this.list = this.list.filter((ele) => ele.c !== true)
    },
    clearAll() {
      this.list = []
    },
  },
  computed: {
    num() {
      return this.list.reduce((sum, ele) => (ele.c ? sum + ele.count : sum), 0)
    },
    isAll: {
      set(val) {
        this.list.forEach((ele) => (ele.c = val))
      },
      get() {
        return this.list.every((ele) => ele.c === true)
      },
    },
    allMoney() {
      return this.list.reduce(
        (sum, ele) => (ele.c ? sum + ele.price * ele.count : sum),
        0
      )
    },
  },
}
</script>

<style>
#app {
  width: 600px;
  margin: 10px auto;
}

.tb {
  border-collapse: collapse;
  width: 100%;
}

.tb th {
  background-color: #0094ff;
  color: white;
}

.tb td,
.tb th {
  padding: 5px;
  border: 1px solid black;
  text-align: center;
}

.add {
  padding: 5px;
  border: 1px solid black;
  margin-bottom: 10px;
}
</style>
