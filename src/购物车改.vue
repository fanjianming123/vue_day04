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
      <tr v-for="item in bookList" :key="item.id">
        <td style="width: 10%">
          <el-checkbox v-model="item.c"></el-checkbox>
        </td>
        <td style="width: 35%; display: flex; align-items: center">
          <el-image
            style="width: 100px; height: 100px"
            :src="item.url"
          ></el-image>
          <p style="flex: 1">
            {{ item.bookName }}
          </p>
        </td>
        <td>￥{{ item.bookPrice }}</td>
        <td style="display: flex; align-items: center">
          <el-button plain @click="reduce(item)">-</el-button>
          <el-input
            min="1"
            v-model="item.count"
            style="width: 50%; font-size: 18px"
          ></el-input>
          <el-button plain @click="add(item)">+</el-button>
        </td>
        <td>￥{{ (item.count * item.bookPrice).toFixed(2) }}</td>
        <td>
          <a href="javascript:;" @click.prevent="delBook(item.id)">删除</a>
        </td>
      </tr>
    </el-main>
    <el-footer>
      <div class="left-footer">
        <el-checkbox v-model="isAll"></el-checkbox>
        <el-button
          type="info"
          plain
          style="margin: 0 20px"
          @click.prevent="delChecked"
          >删除选中商品</el-button
        >
        <el-button type="warning" plain @click="delAll">清理购物车</el-button>
      </div>
      <div class="right-footer" style="display: flex">
        <span>已经选{{ totalCount }}件商品</span>
        <span style="margin: 0 20px">商品总价：￥{{ totalPrice }}</span>
        <el-button type="danger" style="width: 200px">结算</el-button>
      </div>
    </el-footer>
  </el-container>
</template>

<script>
import imgUrl from './assets/1.png'
export default {
  data() {
    return {
      // url: imgUrl,
      bookList: [
        {
          id: 100,
          bookName:
            '【5本26.8元】经典儿童文学彩图青少版 八十天环游地球中学生语文教学大纲',
          bookPrice: 12.6,
          url: imgUrl,
          count: 1,
          c: false,
        },
        {
          id: 101,
          bookName:
            '【2000张贴纸】贴纸书3-6岁贴画儿童贴画书全套12册贴画贴纸儿童汽',
          bookPrice: 24.8,
          url: imgUrl,
          count: 1,
          c: false,
        },
        {
          id: 102,
          bookName:
            '【5本26.8元】经典儿童文学彩图青少版 八十天环游地球中学生语文教学大纲',
          bookPrice: 29.8,
          url: imgUrl,
          count: 1,
          c: false,
        },
      ],
    }
  },
  computed: {
    isAll: {
      set(val) {
        this.bookList.forEach((item) => (item.c = val))
      },
      get() {
        if (this.bookList.length == 0) return false
        return this.bookList.every((item) => item.c)
      },
    },
    totalCount() {
      return this.bookList.reduce((sum, next) => {
        return next.c ? sum + +next.count : sum
      }, 0)
    },
    totalPrice() {
      return this.bookList
        .reduce((sum, next) => {
          return next.c ? sum + next.count * next.bookPrice : sum
        }, 0)
        .toFixed(2)
    },
  },
  methods: {
    reduce(ele) {
      if (ele.count <= 1) return
      return ele.count--
    },
    add(ele) {
      return ele.count++
    },
    delBook(id) {
      this.bookList = this.bookList.filter((item) => item.id !== id)
    },
    delAll() {
      this.bookList = []
    },
    delChecked() {
      this.bookList = this.bookList.filter((item) => item.c !== true)
    },
    countBlur(e) {
      console.log(e)
      if (!e.target.value) {
        this.add()
        return alert('商品数量输入不能为空')
      }
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
a {
  text-decoration: none;
  color: red;
}
th,
td {
  width: 10%;
}
td > p {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
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
