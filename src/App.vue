<template>
  <div>
    <div class="shortcut">
      <div class="w">
        <div class="fl">
          <ul>
            <li>品优购欢迎您！</li>
            <li>
              <a href="#">请登录</a>
              <a href="#" class="style-red">免费注册</a>
            </li>
          </ul>
        </div>
        <div class="fr">
          <ul>
            <li><a href="#">我的订单</a></li>
            <li class="spacer"></li>
            <li>
              <a href="#">我的品优购</a>
              <i class="icomoon"></i>
            </li>
            <li class="spacer"></li>
            <li><a href="#">品优购会员</a></li>
            <li class="spacer"></li>
            <li><a href="#">企业采购</a></li>
            <li class="spacer"></li>
            <li><a href="#">关注品优购</a> <i class="icomoon"></i></li>
            <li class="spacer"></li>
            <li><a href="#">客户服务</a> <i class="icomoon"></i></li>
            <li class="spacer"></li>
            <li><a href="#">网站导航</a> <i class="icomoon"></i></li>
          </ul>
        </div>
      </div>
    </div>
    <div class="car-header">
      <div class="w">
        <div class="car-logo">
          <img src="./assets/img/logo.png" alt="" /> <b>购物车</b>
        </div>
      </div>
    </div>
    <div class="c-container">
      <div class="w">
        <div class="cart-filter-bar">
          <em>全部商品</em>
        </div>
        <!-- 购物车主要核心区域 -->
        <div class="cart-warp">
          <!-- 头部全选模块 -->
          <div class="cart-thead">
            <div class="t-checkbox">
              <input
                type="checkbox"
                name=""
                id=""
                class="checkall"
                v-model="isAll"
              />
              全选
            </div>
            <div class="t-goods">商品</div>
            <div class="t-price">单价</div>
            <div class="t-num">数量</div>
            <div class="t-sum">小计</div>
            <div class="t-action">操作</div>
          </div>
          <!-- 商品详细模块 -->
          <div class="cart-item-list">
            <div class="cart-item" v-for="item in booklist" :key="item.id">
              <div class="p-checkbox">
                <input type="checkbox" class="j-checkbox" v-model="item.c" />
              </div>
              <div class="p-goods">
                <div class="p-img">
                  <img :src="item.img" />
                </div>
                <div class="p-msg">
                  {{ item.bookname }}
                </div>
              </div>
              <div class="p-price">￥{{ item.price }}</div>
              <div class="p-num">
                <div class="quantity-form">
                  <a
                    href="javascript:;"
                    class="decrement"
                    @click="btn1Fn(item.id)"
                    >-</a
                  >
                  <input type="text" class="itxt" v-model="item.count" />
                  <a
                    href="javascript:;"
                    class="increment"
                    @click.stop="btnFn(item.id)"
                    >+</a
                  >
                </div>
              </div>
              <div class="p-sum">
                ￥{{ (item.price * item.count).toFixed(2) }}
              </div>
              <div class="p-action">
                <a href="javascript:;" @click="del(item.id)">删除</a>
              </div>
            </div>
          </div>

          <!-- 结算模块 -->
          <div class="cart-floatbar">
            <div class="select-all">
              <input
                type="checkbox"
                name=""
                id=""
                class="checkall"
                v-model="isAll"
              />全选
            </div>
            <div class="operation">
              <a href="javascript:;" class="remove-batch" @click="delFn"> 删除选中的商品</a>
              <a href="javascript:;" class="clear-all" @click="clearFn">清理购物车</a>
            </div>
            <div class="toolbar-right">
              <div class="amount-sum">
                总件数<em>{{ bookCount }}</em
                >件商品
              </div>
              <div class="price-sum">
                总价： <em>￥{{ allPrice.toFixed(2) }}</em>
              </div>
              <div class="btn-area">去结算</div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- footer start -->
    <div class="footer">
      <div class="w">
        <!-- mod_service -->
        <div class="mod_service">
          <ul>
            <li>
              <i class="mod-service-icon mod_service_zheng"></i>
              <div class="mod_service_tit">
                <h5>正品保障</h5>
                <p>正品保障，提供发票</p>
              </div>
            </li>
            <li>
              <i class="mod-service-icon mod_service_kuai"></i>
              <div class="mod_service_tit">
                <h5>正品保障</h5>
                <p>正品保障，提供发票</p>
              </div>
            </li>
            <li>
              <i class="mod-service-icon mod_service_bao"></i>
              <div class="mod_service_tit">
                <h5>正品保障</h5>
                <p>正品保障，提供发票</p>
              </div>
            </li>
            <li>
              <i class="mod-service-icon mod_service_bao"></i>
              <div class="mod_service_tit">
                <h5>正品保障</h5>
                <p>正品保障，提供发票</p>
              </div>
            </li>
            <li>
              <i class="mod-service-icon mod_service_bao"></i>
              <div class="mod_service_tit">
                <h5>正品保障</h5>
                <p>正品保障，提供发票</p>
              </div>
            </li>
          </ul>
        </div>
        <!-- mod_help -->
        <div class="mod_help">
          <dl class="mod_help_item">
            <dt>购物指南</dt>
            <dd><a href="#">购物流程 </a></dd>
            <dd><a href="#">会员介绍 </a></dd>
            <dd><a href="#">生活旅行</a></dd>
            <dd><a href="#">常见问题 </a></dd>
            <dd><a href="#">大家电 </a></dd>
            <dd><a href="#">联系客服 </a></dd>
          </dl>
          <dl class="mod_help_item">
            <dt>购物指南</dt>
            <dd><a href="#">购物流程 </a></dd>
            <dd><a href="#">会员介绍 </a></dd>
            <dd><a href="#">生活旅行</a></dd>
            <dd><a href="#">常见问题 </a></dd>
            <dd><a href="#">大家电 </a></dd>
            <dd><a href="#">联系客服 </a></dd>
          </dl>
          <dl class="mod_help_item">
            <dt>购物指南</dt>
            <dd><a href="#">购物流程 </a></dd>
            <dd><a href="#">会员介绍 </a></dd>
            <dd><a href="#">生活旅行</a></dd>
            <dd><a href="#">常见问题 </a></dd>
            <dd><a href="#">大家电 </a></dd>
            <dd><a href="#">联系客服 </a></dd>
          </dl>
          <dl class="mod_help_item">
            <dt>购物指南</dt>
            <dd><a href="#">购物流程 </a></dd>
            <dd><a href="#">会员介绍 </a></dd>
            <dd><a href="#">生活旅行 </a></dd>
            <dd><a href="#">常见问题 </a></dd>
            <dd><a href="#">大家电 </a></dd>
            <dd><a href="#">联系客服 </a></dd>
          </dl>
          <dl class="mod_help_item">
            <dt>购物指南</dt>
            <dd><a href="#">购物流程 </a></dd>
            <dd><a href="#">会员介绍 </a></dd>
            <dd><a href="#">生活旅行 </a></dd>
            <dd><a href="#">常见问题 </a></dd>
            <dd><a href="#">大家电 </a></dd>
            <dd><a href="#">联系客服 </a></dd>
          </dl>
          <dl class="mod_help_item mod_help_app">
            <dt>帮助中心</dt>
            <dd>
              <img src="./assets/upload/erweima.png" alt="" />
              <p>品优购客户端</p>
            </dd>
          </dl>
        </div>

        <!-- mod_copyright  -->
        <div class="mod_copyright">
          <p class="mod_copyright_links">
            关于我们 | 联系我们 | 联系客服 | 商家入驻 | 营销中心 | 手机品优购 |
            友情链接 | 销售联盟 | 品优购社区 | 品优购公益 | English Site |
            Contact U
          </p>
          <p class="mod_copyright_info">
            地址：北京市昌平区建材城西路金燕龙办公楼一层 邮编:100096
            电话:400-618-4000 传真:010-82935100 邮箱: zhanghj+itcast.cn <br />
            京ICP备08001421号京公网安备110108007702
          </p>
        </div>
      </div>
    </div>
    <!-- footer end -->
  </div>
</template>

<script>
import img_01 from './assets/upload/p1.jpg';
import img_02 from './assets/upload/p2.jpg';
import img_03 from './assets/upload/p3.jpg';
export default {
  data() {
    return {
      booklist: [
        {
          id: 1,
          img: img_01,
          bookname:
            '【5本26.8元】经典儿童文学彩图青少版八十天环游地球中学生语文教学大纲',
          count: 1,
          price: 12.6,
          c: false,
        },
        {
          id: 2,
          img: img_02,
          bookname:
            '【2000张贴纸】贴纸书 3-6岁 贴画儿童 贴画书全套12册 贴画贴纸儿童 汽',
          count: 1,
          price: 24.8,
          c: false,
        },
        {
          id: 3,
          img: img_03,
          bookname:
            '唐诗三百首+成语故事全2册 一年级课外书 精装注音儿童版小学生二三年级课外阅读书籍',
          count: 1,
          price: 29.8,
          c: false,
        },
      ],
    };
  },
  methods: {
    btnFn(val) {
      // console.log(val)
      const index = this.booklist.findIndex((ele) => ele.id == val);
      // console.log(index);
      this.booklist[index].count++;
    },
    btn1Fn(val) {
      const index = this.booklist.findIndex((ele) => ele.id == val);
      this.booklist[index].count > 1 ? this.booklist[index].count-- : 1;
    },
    del(val) {
      this.booklist = this.booklist.filter((ele) => ele.id != val);
    },
    delFn(){
    },
    clearFn(){
      this.booklist = []
    }
  },
  computed: {
    isAll: {
      set(val) {
        this.booklist.forEach((item) => (item.c = val));
      },
      get() {
        return this.booklist.every((item) => item.c);
      },
    },
    bookCount() {
      return this.booklist.reduce((sum, next) => {
      return next.c? sum = sum + next.count : sum
        }, 0);
    },
    allPrice() {
      return this.booklist.reduce((sum, next) => {
        return next.c ? (sum = sum + next.count * next.price) : sum;
      }, 0);
    },
  },
};
</script>

<style scoped>
/*清除元素默认的内外边距  */
* {
  margin: 0;
  padding: 0;
}
/*让所有斜体 不倾斜*/
em,
i {
  font-style: normal;
}
/*去掉列表前面的小点*/
li {
  list-style: none;
}
/*图片没有边框   去掉图片底侧的空白缝隙*/
img {
  border: 0; /*ie6*/
  vertical-align: middle;
}
/*让button 按钮 变成小手*/
button {
  cursor: pointer;
}
/*取消链接的下划线*/
a {
  color: #666;
  text-decoration: none;
}

a:hover {
  color: #e33333;
}

button,
input {
  font-family: 'Microsoft YaHei', 'Heiti SC', tahoma, arial, 'Hiragino Sans GB',
    \\5B8B\4F53, sans-serif;
  /*取消轮廓线 蓝色的*/
  outline: none;
}

body {
  background-color: #fff;
  font: 12px/1.5 'Microsoft YaHei', 'Heiti SC', tahoma, arial,
    'Hiragino Sans GB', \\5B8B\4F53, sans-serif;
  color: #666;
}

.hide,
.none {
  display: none;
}
/*清除浮动*/
.clearfix:after {
  visibility: hidden;
  clear: both;
  display: block;
  content: '.';
  height: 0;
}

.clearfix {
  *zoom: 1;
}
.car-header {
  padding: 20px 0;
}

.car-logo img {
  vertical-align: middle;
}

.car-logo b {
  font-size: 20px;
  margin-top: 20px;
  margin-left: 10px;
}

.cart-filter-bar {
  font-size: 16px;
  color: #e2231a;
  font-weight: 700;
}

.cart-filter-bar em {
  padding: 5px;
  border-bottom: 1px solid #e2231a;
}

.cart-thead {
  height: 32px;
  line-height: 32px;
  margin: 5px 0 10px;
  padding: 5px 0;
  background: #f3f3f3;
  border: 1px solid #e9e9e9;
  border-top: 0;
  position: relative;
}

.cart-thead > div,
.cart-item > div {
  float: left;
}

.t-checkbox,
.p-checkbox {
  height: 18px;
  line-height: 18px;
  padding-top: 7px;
  width: 122px;
  padding-left: 11px;
}

.t-goods {
  width: 400px;
}

.t-price {
  width: 120px;
  padding-right: 40px;
  text-align: right;
}

.t-num {
  width: 150px;
  text-align: center;
}

.t-sum {
  width: 100px;
  text-align: right;
}

.t-action {
  width: 130px;
  text-align: right;
}

.cart-item {
  height: 160px;
  border-style: solid;
  border-width: 2px 1px 1px;
  border-color: #aaa #f1f1f1 #f1f1f1;
  background: #fff;
  padding-top: 14px;
  margin: 15px 0;
}

.check-cart-item {
  background: #fff4e8;
}

.p-checkbox {
  width: 50px;
}

.p-goods {
  margin-top: 8px;
  width: 565px;
}

.p-img {
  float: left;
  border: 1px solid #ccc;
  padding: 5px;
}

.p-msg {
  float: left;
  width: 210px;
  margin: 0 10px;
}

.p-price {
  width: 110px;
}

.quantity-form {
  width: 80px;
  height: 22px;
}

.p-num {
  width: 170px;
}

.decrement,
.increment {
  float: left;
  border: 1px solid #cacbcb;
  height: 18px;
  line-height: 18px;
  padding: 1px 0;
  width: 16px;
  text-align: center;
  color: #666;
  margin: 0;
  background: #fff;
  margin-left: -1px;
}

.itxt {
  float: left;
  border: 1px solid #cacbcb;
  width: 42px;
  height: 18px;
  line-height: 18px;
  text-align: center;
  padding: 1px;
  margin: 0;
  margin-left: -1px;
  font-size: 12px;
  font-family: verdana;
  color: #333;
  -webkit-appearance: none;
}

.p-sum {
  font-weight: 700;
  width: 145px;
}

/* 结算模块 */

.cart-floatbar {
  height: 50px;
  border: 1px solid #f0f0f0;
  background: #fff;
  position: relative;
  margin-bottom: 50px;
  line-height: 50px;
}

.select-all {
  float: left;
  height: 18px;
  line-height: 18px;
  padding: 16px 0 16px 9px;
  white-space: nowrap;
}

.select-all input {
  vertical-align: middle;
  display: inline-block;
  margin-right: 5px;
}

.operation {
  float: left;
  width: 200px;
  margin-left: 40px;
}

.clear-all {
  font-weight: 700;
  margin: 0 20px;
}

.toolbar-right {
  float: right;
}

.amount-sum {
  float: left;
}

.amount-sum em {
  font-weight: 700;
  color: #e2231a;
  padding: 0 3px;
}

.price-sum {
  float: left;
  margin: 0 15px;
}

.price-sum em {
  font-size: 16px;
  color: #e2231a;
  font-weight: 700;
}

.btn-area {
  font-weight: 700;
  width: 94px;
  height: 52px;
  line-height: 52px;
  color: #fff;
  text-align: center;
  font-size: 18px;
  font-family: 'Microsoft YaHei';
  background: #e54346;
  overflow: hidden;
}

/*公共样式*/

.fl {
  float: left;
}

.fr {
  float: right;
}

@font-face {
  font-family: 'icomoon';
  src: url('./assets/fonts/icomoon.eot?7kkyc2');
  src: url('./assets/fonts/icomoon.eot?7kkyc2#iefix')
      format('embedded-opentype'),
    url('./assets/fonts/icomoon.ttf?7kkyc2') format('truetype'),
    url('./assets/fonts/icomoon.woff?7kkyc2') format('woff'),
    url('./assets/fonts/icomoon.svg?7kkyc2#icomoon') format('svg');
  font-weight: normal;
  font-style: normal;
}

.fr .icomoon {
  font-family: 'icomoon';
  font-size: 16px;
  line-height: 26px;
}

/*版心*/

.w {
  width: 1200px;
  margin: 0 auto;
}

.style-red {
  color: #c81623;
}

.spacer {
  width: 1px;
  height: 12px;
  background-color: #666;
  margin: 9px 12px 0;
}

/*顶部快捷导航*/

.shortcut {
  height: 31px;
  background-color: #f1f1f1;
  line-height: 31px;
}

.shortcut li {
  float: left;
}

/*header区域*/

.header {
  position: relative;
  height: 105px;
}

.logo {
  position: absolute;
  top: 25px;
  left: 0;
  width: 175px;
  height: 56px;
}

.logo a {
  display: block;
  /*overflow: hidden;*/
  width: 175px;
  height: 56px;
  background: url(./assets/img/logo.png) no-repeat;
  /*text-indent: -999px;*/
  font-size: 0;
}

.search {
  position: absolute;
  top: 25px;
  left: 348px;
}

.text {
  float: left;
  width: 445px;
  height: 32px;
  border: 2px solid #b1191a;
  padding-left: 10px;
  color: #ccc;
}

.btn {
  float: left;
  width: 82px;
  height: 36px;
  background-color: #b1191a;
  border: 0;
  font-size: 16px;
  color: #fff;
}

.hotwrods {
  position: absolute;
  top: 65px;
  left: 348px;
}

.hotwrods a {
  margin: 0 10px;
}

.shopcar {
  position: absolute;
  top: 25px;
  right: 64px;
  width: 138px;
  height: 34px;
  border: 1px solid #dfdfdf;
  background-color: #f7f7f7;
  line-height: 34px;
  text-align: center;
}

.car {
  font-family: 'icomoon';
  color: #da5555;
}

.arrow {
  font-family: 'icomoon';
  margin-left: 5px;
}

.count {
  position: absolute;
  top: -5px;
  /*应该是左侧对齐 文字才能往右走显示*/
  left: 100px;
  background-color: #e60012;
  height: 14px;
  padding: 0 3px;
  line-height: 14px;
  color: #fff;
  /*border-radius: 左上角 右上角  右下角  左下角;*/
  border-radius: 7px 7px 7px 0;
}

/*nav start*/

.nav {
  height: 45px;
  border-bottom: 2px solid #b1191a;
}

.dropdown {
  width: 209px;
  height: 45px;
}

.dropdown .dt {
  height: 100%;
  background-color: #b1191a;
  font-size: 16px;
  color: #fff;
  text-align: center;
  line-height: 45px;
}

.dropdown .dd {
  height: 465px;
  background-color: #c81623;
  margin-top: 2px;
}

.menu_item:hover {
  background-color: #fff;
}

/*鼠标经过li 里面的 a变颜色*/

.menu_item:hover a {
  color: #c81623;
}

.menu_item {
  height: 31px;
  line-height: 31px;
  margin-left: 1px;
  padding: 0 10px;
  transition: all 0.5s;
}

.menu_item:hover {
  padding-left: 20px;
}

.menu_item a {
  font-size: 14px;
  color: #fff;
}

.menu_item i {
  float: right;
  font-family: 'icomoon';
  font-size: 18px;
  color: #fff;
}

.navitems {
  margin-left: 10px;
}

.navitems li {
  float: left;
}

.navitems li a {
  display: block;
  height: 45px;
  padding: 0 25px;
  line-height: 45px;
  font-size: 16px;
}

/*footer 部分*/

.footer {
  height: 386px;
  background-color: #f5f5f5;
  padding-top: 30px;
}

.mod_service {
  height: 79px;
  border-bottom: 1px solid #ccc;
}

.mod_service li {
  float: left;
  width: 240px;
  height: 79px;
}

.mod-service-icon {
  /*浮动的盒子 可以直接给大小的 不需要转换*/
  float: left;
  width: 50px;
  height: 50px;
  margin-left: 35px;
  background: url(./assets/img/icons.png) no-repeat;
}

.mod_service_zheng {
  background-position: -253px -3px;
}

.mod_service_tit {
  float: left;
  margin-left: 5px;
}

.mod_service_tit h5 {
  margin: 5px 0;
}

.mod_service_kuai {
  background-position: -255px -54px;
}

.mod_service_bao {
  background-position: -257px -105px;
}

.mod_help {
  height: 187px;
  border-bottom: 1px solid #ccc;
}

.mod_help_item {
  float: left;
  width: 150px;
  padding: 20px 0 0 50px;
}

.mod_help_item dt {
  height: 25px;
  font-size: 16px;
}

.mod_help_item dd {
  height: 22px;
}

.mod_help_app dt,
.mod_help_app p {
  padding-left: 15px;
}

.mod_help_app img {
  margin: 7px 0;
}

.mod_copyright {
  text-align: center;
}

.mod_copyright_links {
  margin: 20px 0 15px 0;
}

.mod_copyright_info {
  line-height: 18px;
}
/*详情页的样式文件*/
.de_container {
  margin-top: 20px;
}
.crumb_wrap {
  height: 25px;
}
.crumb_wrap a {
  margin-right: 10px;
}
.preview_wrap {
  width: 400px;
  height: 590px;
}
.preview_img {
  height: 398px;
  border: 1px solid #ccc;
}
.preview_list {
  position: relative;
  height: 60px;
  margin-top: 60px;
}
.list_item {
  width: 320px;
  height: 60px;
  margin: 0 auto;
}
.list_item li {
  float: left;
  width: 56px;
  height: 56px;
  border: 2px solid transparent;
  margin: 0 2px;
}
.list_item li.current {
  border-color: #c81623;
}
.arrow_prev,
.arrow_next {
  position: absolute;
  top: 15px;
  width: 22px;
  height: 32px;
  background-color: purple;
}
.arrow_prev {
  left: 0;
  background: url(./assets/img/arrow-prev.png) no-repeat;
}
.arrow_next {
  right: 0;
  background: url(./assets/img/arrow-next.png) no-repeat;
}
.itemInfo_wrap {
  width: 718px;
}
.sku_name {
  height: 30px;
  font-size: 16px;
  font-weight: 700;
}
.news {
  height: 32px;
  color: #e12228;
}
.summary dl {
  overflow: hidden;
}
.summary dt,
.summary dd {
  float: left;
}
.summary dt {
  width: 60px;
  padding-left: 10px;
  line-height: 36px;
}
.summary_price,
.summary_promotion {
  position: relative;
  padding: 10px 0;
  background-color: #fee9eb;
}
.price {
  font-size: 24px;
  color: #e12228;
}
.summary_price a {
  color: #c81623;
}
.remark {
  position: absolute;
  right: 10px;
  top: 20px;
}
.summary_promotion {
  padding-top: 0;
}
.summary_promotion dd {
  width: 450px;
  line-height: 36px;
}
.summary_promotion em {
  display: inline-block;
  width: 40px;
  height: 22px;
  background-color: #c81623;
  text-align: center;
  line-height: 22px;
  color: #fff;
}
.summary_support dd {
  line-height: 36px;
}
.choose_color a {
  display: inline-block;
  width: 80px;
  height: 41px;
  background-color: #f7f7f7;
  border: 1px solid #ededed;
  text-align: center;
  line-height: 41px;
}
.summary a.current {
  border-color: #c81623;
}
.choose_version {
  margin: 10px 0;
}
.choose_version a,
.choose_type a {
  display: inline-block;
  height: 32px;
  padding: 0 12px;
  background-color: #f7f7f7;
  border: 1px solid #ededed;
  text-align: center;
  line-height: 32px;
}
.choose_btns {
  margin-top: 20px;
}
.choose_amount {
  position: relative;
  float: left;
  width: 50px;
  height: 46px;
  background-color: pink;
}
.choose_amount input {
  width: 33px;
  height: 44px;
  border: 1px solid #ccc;
  text-align: center;
}
.add,
.reduce {
  position: absolute;
  right: 0;
  width: 15px;
  height: 22px;
  border: 1px solid #ccc;
  background-color: #f1f1f1;
  text-align: center;
  line-height: 22px;
}
.add {
  top: 0;
}
.reduce {
  bottom: 0;
  /*禁止鼠标样式*/
  cursor: not-allowed; /* pointer  小手  move  移动  */
}
.addcar {
  float: left;
  width: 142px;
  height: 46px;
  background-color: #c81623;
  text-align: center;
  line-height: 46px;
  font-size: 18px;
  color: #fff;
  margin-left: 10px;
  font-weight: 700;
}
.product_detail {
  margin-bottom: 50px;
}
.aside {
  width: 208px;
  border: 1px solid #ccc;
}
.tab_list {
  overflow: hidden;
  height: 34px;
}
/*把背景颜色 底边框都给 li*/
.tab_list li {
  float: left;
  background-color: #f1f1f1;
  border-bottom: 1px solid #ccc;
  height: 33px;
  text-align: center;
  line-height: 33px;
}
/*鼠标单击 li 变化样式   背景变白色 去掉下边框 文字变颜色*/
.tab_list .current {
  background-color: #fff;
  border-bottom: 0;
  color: red;
}
.first_tab {
  width: 104px;
}
.second_tab {
  width: 103px;
  border-left: 1px solid #ccc;
}
.tab_con {
  padding: 0 10px;
}
.tab_con li {
  border-bottom: 1px solid #ccc;
}
.tab_con li h5 {
  /*超出的文字省略号显示*/
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  font-weight: 400;
}
.aside_price {
  font-weight: 700;
  margin: 10px 0;
}
.as_addcar {
  display: block;
  width: 88px;
  height: 26px;
  border: 1px solid #ccc;
  background-color: #f7f7f7;
  margin: 10px auto;
  text-align: center;
  line-height: 26px;
}
.detail {
  width: 978px;
}
.detail_tab_list {
  height: 39px;
  border: 1px solid #ccc;
  background-color: #f1f1f1;
}
.detail_tab_list li {
  float: left;
  height: 39px;
  line-height: 39px;
  padding: 0 20px;
  text-align: center;
  cursor: pointer;
}
.detail_tab_list .current {
  background-color: #c81623;
  color: #fff;
}
.item_info {
  padding: 20px 0 0 20px;
}
.item_info li {
  line-height: 22px;
}
.more {
  float: right;
  font-weight: 700;
  font-family: 'icomoon';
}

/*这个文件里面放的是 首页的样式*/

.main {
  width: 980px;
  height: 455px;
  margin-left: 219px;
  margin-top: 10px;
}

.focus {
  position: relative;
  width: 721px;
  height: 455px;
  background-color: purple;
  overflow: hidden;
}

.focus ul {
  position: absolute;
  top: 0;
  left: 0;
  width: 600%;
}

.focus ul li {
  float: left;
}

.arrow-l,
.arrow-r {
  display: none;
  position: absolute;
  top: 50%;
  margin-top: -20px;
  width: 24px;
  height: 40px;
  background: rgba(0, 0, 0, 0.3);
  text-align: center;
  line-height: 40px;
  color: #fff;
  font-family: 'icomoon';
  font-size: 18px;
  z-index: 2;
}

.arrow-r {
  right: 0;
}

.circle {
  position: absolute;
  bottom: 10px;
  left: 50px;
}

.circle li {
  float: left;
  width: 8px;
  height: 8px;
  /*background-color: #fff;*/
  border: 2px solid rgba(255, 255, 255, 0.5);
  margin: 0 3px;
  border-radius: 50%;
  /*鼠标经过显示小手*/
  cursor: pointer;
}

.current {
  background-color: #fff;
}

.newsflash {
  width: 250px;
  height: 455px;
}

.news {
  height: 163px;
  border: 1px solid #ccc;
}

.news-hd {
  height: 32px;
  /*dotted 点线  dashed  虚线*/
  border-bottom: 1px dotted #ccc;
  padding: 0 15px;
  font-size: 14px;
  line-height: 32px;
}

.news-hd a {
  float: right;
  font-size: 12px;
  font-family: 'icomoon';
}

.news-bd {
  padding: 10px 0 0 15px;
}

.news-bd li {
  height: 23px;
}

.lifeservice {
  overflow: hidden;
  height: 208px;
  border: 1px solid #ccc;
  border-top: none;
}

.lifeservice ul {
  width: 252px;
}

.lifeservice li {
  position: relative;
  float: left;
  width: 62px;
  height: 70px;
  border-right: 1px solid #ccc;
  border-bottom: 1px solid #ccc;
}

.lifeservice li a {
  display: block;
  /* overflow: hidden; 解决i 引起的 外边距塌陷合并的问题*/
  overflow: hidden;
  height: 100%;
}

.lifeservice li p {
  text-align: center;
}

.hot {
  position: absolute;
  right: 0;
  top: 0;
  width: 12px;
  height: 15px;
  background: url(./assets/img/jian.jpg) no-repeat;
}

.service_ico {
  display: block;
  width: 24px;
  height: 24px;
  background: url(./assets/img/icons.png) no-repeat;
  margin: 10px auto;
}

.service_ico_huafei {
  background-position: -17px -16px;
}

.service_ico_feiji {
  width: 26px;
  background-position: -78px -16px;
}

.bargain {
  height: 75px;
  margin-top: 5px;
}

/*推荐模块*/

.recommend {
  height: 163px;
  margin-top: 10px;
}

.recom-hd {
  width: 200px;
  height: 163px;
  background-color: #5c5251;
  text-align: center;
}

.recom-hd img {
  margin: 30px 0 10px 0;
}

.recom-hd h3 {
  font-size: 18px;
  color: #fff;
  font-weight: normal;
}

.recom-bd {
  width: 1000px;
  height: 163px;
  background-color: #ebebeb;
}

.recom-bd li {
  float: left;
  width: 249px;
  height: 145px;
  border-right: 1px solid #ccc;
  margin-top: 10px;
}

.recom-bd .last {
  border-right: 0;
}

/*floor 楼层区*/

.box-hd {
  height: 30px;
  border-bottom: 2px solid #c81623;
  margin-top: 25px;
}

.box-hd h3 {
  float: left;
  font-size: 18px;
  color: #c81623;
}

.tab-list {
  float: right;
  line-height: 30px;
}

.tab-list li {
  float: left;
}

.tab-list li a {
  margin: 0 15px;
}

.box-bd {
  height: 360px;
}

.w209 {
  width: 209px;
  background-color: #f9f9f9;
}

.w329 {
  width: 329px;
}

.w219 {
  width: 219px;
  border-right: 1px solid #ccc;
}

.w220 {
  width: 220px;
  border-right: 1px solid #ccc;
}

.tab-con li {
  float: left;
  height: 360px;
}

.tab-con-item {
  border-bottom: 1px solid #ccc;
}

.tab-con-list {
  overflow: hidden;
  margin-bottom: 15px;
}

.tab-con-list li {
  width: 86px;
  height: 32px;
  line-height: 32px;
  border-bottom: 1px solid #ccc;
  margin-left: 10px;
  text-align: center;
}

.box-bd li {
  overflow: hidden;
}

.box-bd img {
  /*过渡写到本身上， 谁做动画，给谁加*/
  transition: all 0.2s;
}

/*我们鼠标经过图片 往右走 8px*/

.box-bd img:hover {
  margin-left: 8px;
}

/*电梯导航*/

.fixedtool {
  position: fixed;
  top: 100px;
  left: 50%;
  margin-left: -676px;
  width: 66px;
  background-color: #fff;
  display: none;
}

.fixedtool li {
  height: 32px;
  line-height: 32px;
  text-align: center;
  font-size: 12px;
  border-bottom: 1px solid #ccc;
  cursor: pointer;
}

.fixedtool .current {
  background-color: #c81623;
  color: #fff;
}

/*列表页面的css*/
.sk {
  position: absolute;
  top: 40px;
  left: 185px;
  height: 32px;
  border-left: 1px solid #b1191a;
  padding: 5px 0 0 15px;
}
.sk_list li {
  float: left;
  line-height: 45px;
  margin: 0 30px;
}
.sk_list li a {
  font-size: 16px;
  color: #000;
  font-weight: 700;
}
.sk_list li a:hover {
  color: #c81523;
}
.sk_con li {
  float: left;
  line-height: 45px;
  margin: 0 20px;
}
.sk_con li a {
  font-size: 14px;
  font-weight: 700;
  font-family: 'icomoon';
}
/*列表页内容区域?*/
.sk_bd {
  margin-top: 25px;
}
.sk_bd ul {
  width: 1212px;
}
.sk_goods {
  position: relative;
  float: left;
  width: 288px;
  height: 458px;
  border: 1px solid transparent;
  margin: 0 12px 15px 0;
}
.sk_goods:hover {
  border: 1px solid #e12228;
}
.sk_goods_title {
  font-size: 14px;
  color: #666;
  font-weight: normal;
  padding: 10px;
}
.sk_goods_price {
  padding: 0 10px;
}
.sk_goods_price em {
  font-size: 22px;
  color: #e60012;
}
.sk_goods_price del {
  font-size: 14px;
  font-weight: 700;
  color: #a4a4a4;
}
.sk_goods_progress {
  padding: 0 10px;
}
.bar {
  display: inline-block;
  width: 130px;
  height: 10px;
  border: 1px solid #b1191a;
  vertical-align: middle;
  margin: 0 5px;
  border-radius: 5px;
}
.bar_in {
  width: 87%;
  height: 10px;
  background-color: #f24349;
}
.sk_goods_progress em,
.sk_goods_progress i {
  color: #f24349;
}
.sk_goods_buy {
  position: absolute;
  bottom: 0;
  width: 100%;
  height: 50px;
  background-color: #b1191a;
  color: #fff;
  text-align: center;
  line-height: 50px;
  font-size: 20px;
}
.page {
  margin: 40px 0;
  /*里面的文字内容  行内块 行内元素 都可以水平居中对齐*/
  text-align: center;
}
.page_num a {
  display: inline-block;
  width: 36px;
  height: 36px;
  line-height: 36px;
  border: 1px solid #ccc;
  background-color: #f7f7f7;
}
.page_num .pn_prev,
.page_num .pn_next {
  width: 83px;
}
.page_num .dotted,
.page_num .current {
  border: 1px solid transparent;
  background-color: transparent;
}
.page_skip input {
  width: 46px;
  height: 36px;
  border: 1px solid #ccc;
  text-align: center;
  /*过渡写在本身上 谁做动画，给谁加*/
  transition: all 0.3s;
}
/*表单获得焦点后 */
.page_skip input:focus {
  width: 88px;
  border: 1px solid skyblue;
}
.page_skip button {
  width: 54px;
  height: 36px;
  border: 1px solid #ccc;
  background-color: #f7f7f7;
}

.w {
  width: 1200px;
  margin: auto;
}
.header {
  height: 82px;
  border-bottom: 2px solid #b1191a;
}
.logo {
  padding-top: 15px;
}
.registerarea {
  height: 520px;
  border: 1px solid #ccc;
  margin-top: 20px;
}
.registerarea h3 {
  height: 40px;
  border-bottom: 1px solid #ccc;
  background-color: #ececec;
  padding: 0 10px;
  font-weight: 400;
  line-height: 40px;
  font-size: 18px;
}
.registerarea h3 em {
  float: right;
  font-size: 14px;
}
.registerarea a {
  color: #c81623;
}
.reg_form {
  width: 600px;
  height: 400px;
  margin: 40px auto 0;
}
.reg_form li {
  margin-bottom: 15px;
}
.reg_form label {
  display: inline-block;
  width: 100px;
  height: 36px;
  line-height: 36px;
  text-align: right;
}
.inp {
  width: 238px;
  height: 34px;
  border: 1px solid #ccc;
  margin-left: 10px;
}
.error {
  color: #df3033;
  margin-left: 10px;
}
.error_icon,
.success_icon {
  display: inline-block;
  width: 20px;
  height: 20px;
  background: url(./assets/img/error.png) no-repeat;
  vertical-align: middle;
  margin-top: -2px;
}
.success {
  color: #40b83f;
  margin-left: 10px;
}
.success_icon {
  background-image: url(./assets/img/success.png);
}
.safe {
  padding-left: 187px;
  color: #b2b2b2;
}
.safe em {
  padding: 0 12px;
  color: #fff;
}
.ruo {
  background-color: #de1111;
}

.zhong {
  background-color: #40b83f;
}

.qiang {
  background-color: #f79100;
}
.agree {
  padding-top: 20px;
  padding-left: 100px;
}
.agree input {
  vertical-align: middle;
  margin-right: 5px;
}
.agree a {
  color: #1ba1e6;
}
.over {
  width: 200px;
  height: 34px;
  background-color: #c81623;
  margin: 30px 0 0 130px;
  border: none;
  color: #fff;
  font-size: 14px;
}
.footer {
  height: 120px;
  text-align: center;
}
.links {
  margin-top: 20px;
  height: 30px;
}
.copyright {
  line-height: 20px;
}
</style>
