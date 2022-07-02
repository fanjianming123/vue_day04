<template>
  <el-container>
    <el-header>
      <th style="width: 10%">
        <el-checkbox v-model="checked">全选</el-checkbox>
      </th>
      <th style="width: 33%">商品</th>
      <th>单价</th>
      <th>数量</th>
      <th>小计</th>
      <th>操作</th>
    </el-header>
    <el-main>
      <tr v-for="item in bookList" :key="item.id">
        <td style="width: 10%">
          <el-checkbox v-model="item.checked"></el-checkbox>
        </td>
        <td style="width: 35%; display: flex; align-items: center">
          <el-image
            style="width: 100px; height: 100px"
            :src="item.url"
          ></el-image>
          <p>{{ item.bookName }}</p>
        </td>
        <td>￥{{ item.bookPrice }}</td>
        <td>
          <el-input-number
            v-model.number.trim="item.bookNum"
            :min="1"
            :max="20"
            label="描述文字"
          ></el-input-number>
        </td>
        <td>￥{{ item.bookNum * item.bookPrice }}</td>
        <td><a href="javascript:;" @click="delFn(item.id)">删除</a></td>
      </tr>
    </el-main>
    <el-footer>
      <div class="left-footer">
        <el-checkbox v-model="checked"></el-checkbox>
        <el-button type="info" plain style="margin: 0 20px" @click="delChose"
          >删除选中商品</el-button
        >
        <el-button type="warning" plain @click="delAll">清理购物车</el-button>
      </div>
      <div class="right-footer" style="display: flex">
        <span>已经选{{ allChose }}件商品</span>
        <span style="margin: 0 20px">商品总价：￥{{ allChosePrice }}</span>
        <el-button type="danger" style="width: 200px">结算</el-button>
      </div>
    </el-footer>
  </el-container>
</template>

<script>
import bookUrl from './assets/d10b1f90fc2331dfedf98a70889a692f.jpeg';
export default {
  data() {
    return {
      bookList: [
        {
          id: 1,
          url: bookUrl,
          bookName: '【5本26.8元】经典儿童文学彩图青少版',
          bookPrice: 12.6,
          bookNum: 1,
          checked: false,
        },
        {
          id: 2,
          url: bookUrl,
          bookName: '【5本26.8元】经典儿童文学彩图青少版',
          bookPrice: 12.6,
          bookNum: 1,
          checked: false,
        },
        {
          id: 3,
          url: bookUrl,
          bookName: '【5本26.8元】经典儿童文学彩图青少版',
          bookPrice: 12.6,
          bookNum: 1,
          checked: false,
        },
      ],
      allNum: 0,
    };
  },
  computed: {
    checked: {
      set(val) {
        this.bookList.forEach((obj) => (obj.checked = val));
      },
      get() {
        if (this.bookList.length == 0) return false;
        return this.bookList.every((ele) => ele.checked);
      },
    },
    allChose() {
      return this.bookList.reduce((sum, cur) => {
        return (sum += cur.checked ? cur.bookNum : 0);
      }, 0);
    },
    allChosePrice() {
      return this.bookList.reduce((sum, cur) => {
        return (sum += cur.checked ? cur.bookNum * cur.bookPrice : 0);
      }, 0);
    },
  },
  methods: {
    delFn(val) {
      let index = this.bookList.findIndex((ele) => (ele.id = val));
      this.bookList.splice(index, 1);
    },
    delChose() {
      this.bookList = this.bookList.filter((ele) => ele.checked != true);
    },
    delAll() {
      this.bookList.splice(0, this.bookList.length);
    },
  },
  watch: {},
};
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
.el-main p {
  margin-left: 50px;
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
td > p {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
.el-container:nth-child(5) .el-aside,
.el-container:nth-child(6) .el-aside {
  line-height: 260px;
}

.el-container:nth-child(7) .el-aside {
  line-height: 320px;
}
a {
  text-decoration: none;
  color: red;
}
</style>
