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
      <tr>
        <td style="width: 10%">
          <el-checkbox v-model="checked"></el-checkbox>
        </td>
        <td style="width: 35%;display: flex;align-items: center;">
          <el-image
            style="width: 100px; height: 100px;">
            :src="url"
            :fit="fit"
          ></el-image>
          <p>
            【5本26.8元】经典儿童文学彩图青少版 八十天环游地球中学生语文教学大纲
          </p>
        </td>
        <td>￥12.60</td>
        <td>
          <el-input-number
            v-model="num"
            @change="handleChange"
            :min="1"
            :max="10"
            label="描述文字"
          ></el-input-number>
        </td>
        <td>￥63.00</td>
        <td><a href="javascript:;">删除</a></td>
      </tr>
    
    </el-main>
    <el-footer>
      <div class="left-footer">
        <el-checkbox v-model="checked"></el-checkbox>
        <el-button type="info" plain style="margin:0 20px">删除选中商品</el-button>
        <el-button type="warning" plain>清理购物车</el-button>
      </div>
      <div class="right-footer" style="display: flex">
        <span>已经选7件商品</span>
        <span style="margin:0 20px">商品总价：￥117.60</span>
        <el-button type="danger" style="width:200px;">结算</el-button>
      </div>
    </el-footer>
  </el-container>
</template>

<script>
export default {
  data() {
    return {
      checked: true,
      url: 'https://fuss10.elemecdn.com/e/5d/4a731a90594a4af544c0c25941171jpeg.jpeg'
    }
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
td{
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
