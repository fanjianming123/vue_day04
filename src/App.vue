<template>
  <div id="app">
    <table class="tb">
      <tr>
        <th><input type="checkbox" v-model="checked" />全选</th>
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
        <td>{{ item.price }}万</td>
        <td>
          <button @click="delFn(item.id)">-</button
          ><input
            type="text"
            style="text-align: center"
            v-model="item.num"
          /><button @click="addFn(item.id)">+</button>
        </td>
        <td>{{ item.num * item.price }}万</td>
        <td><button @click="del(item.id)">删除</button></td>
      </tr>
      <tr v-if="list.length === 0">
        <td colspan="4">没有数据咯~</td>
      </tr>
    </table>
    <br />
    <button @click="del">删除选中商品</button>
    <button @click="delAll">清理购物车</button>
    <br />
    <div style="margin-top: 20px">
      <h2>统计</h2>
      <p>已经选中商品件数{{ allNum }}</p>
      <p>总价{{ alNumPrice }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      list: [
        {
          id: 1,
          name: '奔驰',
          price: 10,
          num: 1,
          time: '2020-08-01',
          c: false,
        },
        {
          id: 2,
          name: '宝马',
          price: 10,
          num: 1,
          time: '2020-08-02',
          c: false,
        },
        {
          id: 3,
          name: '奥迪',
          price: 10,
          num: 1,
          time: '2020-08-03',
          c: false,
        },
      ],
      c: false,
    };
  },
  methods: {
    del() {
      this.list = this.list.filter((ele) => ele.c != true);
    },
    addFn(val) {
      const index = this.list.findIndex((ele) => ele.id == val);
      this.list[index].num++;
    },
    delFn(val) {
      const index = this.list.findIndex((ele) => ele.id == val);
      this.list[index].num--;
    },
    delAll() {
      this.list.splice(0, this.list.length);
    },
  },
  computed: {
    checked: {
      set(val) {
        this.list.forEach((ele) => (ele.c = val));
      },
      get() {
        return this.list.every((ele) => ele.c);
      },
    },
    allNum() {
      return this.list.reduce((sum, cur) => {
        return (sum += cur.c ? cur.num : 0);
      }, 0);
    },
    alNumPrice() {
      return this.list.reduce((sum, cur) => {
        return (sum += cur.c ? cur.num * cur.price : 0);
      }, 0);
    },
  },
};
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
