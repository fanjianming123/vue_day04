<template>
  <el-container>
    <el-header>
      <th style="width: 10%">
        <el-checkbox v-model="isAll">全选</el-checkbox>
      </th>
      <th style="width: 33%">商品</th>
      <th>单价</th>
      <th>数量</th>
      <th>小计</th>
      <th>操作</th>
    </el-header>
    <el-main>
      <tr v-for="item in list" :key="item.id">
        <td style="width: 10%">
          <el-checkbox v-model="item.c"></el-checkbox>
        </td>
        <td style="width: 35%; display: flex; align-items: center">
          <el-image
            style="width: 100px; height: 100px"
            :src="item.url"
            :fit="fit"
          >
          </el-image>
          <p>{{ item.name }}</p>
        </td>
        <td>￥{{ item.price }}</td>
        <td>
          <el-input-number
            v-model="item.count"
            :min="1"
            :max="10"
            label="描述文字"
          ></el-input-number>
        </td>
        <td>￥{{ (item.price * item.count).toFixed(2) }}</td>
        <td><a href="" @click.prevent="delFn(item.id)">删除</a></td>
      </tr>
    </el-main>
    <el-footer>
      <div class="left-footer">
        <el-checkbox v-model="isAll"></el-checkbox>
        <el-button
          type="info"
          plain
          style="margin: 0 20px"
          @click="deleteSelection"
          >删除选中商品</el-button
        >
        <el-button type="warning" plain @click="clear">清理购物车</el-button>
      </div>
      <div class="right-footer" style="display: flex">
        <span>已经选{{ num }}件商品</span>
        <span style="margin: 0 20px">商品总价：￥{{ result.toFixed(2) }}</span>
        <el-button type="danger" style="width: 200px">结算</el-button>
      </div>
    </el-footer>
  </el-container>
</template>

<script>
import img1 from './assets/1.jpg'
import img2 from './assets/2.jpg'
import img3 from './assets/3.jpg'
export default {
  data() {
    return {
      checked: true,
      url: '../src/assets/logo.png',
      list: [
        {
          id: 100,
          name: '【5本26.8元】经典儿童文学彩图青少版',
          price: 18.8,
          url: img1,
          count: 1,
          c: false,
        },
        {
          id: 101,
          name: '【5本26.8元】经典文学彩图青少版',
          price: 13.8,
          url: img2,
          count: 1,
          c: false,
        },
        {
          id: 103,
          name: '【5本26.8元】经典文学彩图青少版',
          price: 17.8,
          url: img3,
          count: 1,
          c: false,
        },
      ],
    }
  },
  methods: {
    //删除
    delFn(id) {
      this.list = this.list.filter((item) => item.id !== id)
    },
    //删除选中
    deleteSelection() {
      this.list = this.list.filter((item) => item.c !== true)
    },
    //清除购物车
    clear() {
      this.list = []
    },
  },
  computed: {
    isAll: {
      set(val) {
        this.list.forEach((item) => (item.c = val))
      },
      get() {
        if (this.list.length === 0) return false
        return this.list.every((ele) => ele.c)
      },
    },
    num() {
      return this.list.reduce((sum, ele) => sum + ele.count, 0)
    },
    result() {
      return this.list.reduce((sum, ele) => sum + ele.price * ele.count, 0)
    },
    watch: {
      list: {
        deep: true,
        immediate: true,
        handler() {},
      },
    },
  },
}
</script>

<style>
.el-header,
.el-footer {
  background-color: #b3c0d1;
  color: #333;
  text-align: center;
  line-height: 60px;
  display: flex;
  justify-content: space-evenly;
}
.el-footer {
  display: flex;
  justify-content: space-between;
}
.el-aside {
  background-color: #d3dce6;
  color: #333;
  text-align: center;
  line-height: 200px;
}

.el-main {
  background-color: #e9eef3;
  color: #333;
  text-align: center;
  line-height: 160px;
}
tr {
  display: flex;
  justify-content: space-evenly;
  background-color: #a6c8ea;
  margin-bottom: 10px;
}
th,
td {
  width: 10%;
}
body > .el-container {
  margin-bottom: 40px;
}

.el-container:nth-child(5) .el-aside,
.el-container:nth-child(6) .el-aside {
  line-height: 260px;
}

.el-container:nth-child(7) .el-aside {
  line-height: 320px;
}
</style>
