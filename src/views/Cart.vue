<template>
  <div class="cart">
    <!-- header部分开始 -->
    <Header/>
    <div class="cart-content">
      <div class="main">
        <p class="cart-title">购物车</p>
        <el-table
          ref="multipleTable"
          :data="tableData"
          tooltip-effect="dark"
          style="width: 100%"
          @selection-change="handleSelectionChange"
        >
          <el-table-column type="selection" width="55"></el-table-column>
          <el-table-column label="商品名称" prop="good" min-width="420">
            <template slot-scope="scope">
              <img style="float:left" :src="goodsList[scope.$index].url" alt width="80" />
              <p
                style="float:left;margin-left:10px;margin-top:30px"
              >{{goodsList[scope.$index].name}}</p>
            </template>
          </el-table-column>
          <el-table-column prop="price" label="单价">
            <template slot-scope="scope">
              <span>￥{{goodsList[scope.$index].price}}</span>
            </template>
          </el-table-column>
          <el-table-column prop="count" label="数量">
            <template slot-scope="scope">
              <input
                type="button"
                value="-"
                style="margin-right:5px"
                @click="subCount(scope.$index)"
              />
              {{goodsList[scope.$index].count}}
              <input
                type="button"
                style="margin-left:5px"
                value="+"
                @click="addCount(scope.$index)"
              />
            </template>
          </el-table-column>
          <el-table-column prop="total" label="小计">
            <template slot-scope="scope">
              <span>￥{{goodsList[scope.$index].price*goodsList[scope.$index].count}}</span>
            </template>
          </el-table-column>
          <el-table-column prop="operation" label="操作">
            <template slot-scope="scope">
              <span @click="del(scope.$index)" class="del">删除</span>
            </template>
          </el-table-column>
        </el-table>
        <div
          class="toPay"
          style="margin-top:100px;border:1px solid white;background:white;padding:30px"
        >
          <el-row :gutter="10">
            <el-col :span="3" class="link">
              <span @click="delAll">批量删除</span>
            </el-col>
            <el-col :span="3">清理下架商品</el-col>
            <el-col :span="7" :offset="6">
              <span>已选</span>
              <span style="color:red;font-size:20px;padding:5px">{{selected}}</span>
              <span>件</span>
              <span style="margin-left:15px">合计:(不含运费)</span>
              <span style="color:red;font-size:20px;padding:5px">￥{{allTotal}}</span>
              <span>元</span>
              <br />
              <span style="font-size:13px">已优惠：￥0</span>
            </el-col>
            <el-col :span="4">
              <el-button
                type="primary"
                style="width:100%;background:red;border:red"
                @click="toCheckout"
              >确认结算</el-button>
            </el-col>
          </el-row>
        </div>
        <div style="height:100px;width:100%"></div>
      </div>
    </div>
    <div class="footer">
      <div class="footer_c inner_c">
        <div class="footer_top">
          <div class="bir">
            <a href="#">
              <img src="@/assets/Home/images/logo.png" alt />
            </a>
            <div
              class="info"
            >青竹良品原创生活类电商品牌，秉承一贯的严谨态度，我们深入世界各地，从源头全程严格把控商品生产环节，力求帮消费者甄选到最优质的商品，全线采用天然原材料，控制甲醛低量无害，采用进口工艺，国际生产线不断优化，食材保证核心原产地新鲜直供，让你享受品质生活</div>
          </div>
          <div class="about">
            <dl>
              <dt>
                <a href="#">关于我们</a>
              </dt>
              <dd>
                <a href="#">我的品牌</a>
              </dd>
              <dd>
                <a href="#">公司动态</a>
              </dd>
              <dd>
                <a href="#">经历发展</a>
              </dd>
              <dd>
                <a href="#">商品推广</a>
              </dd>
            </dl>
            <dl>
              <dt>
                <a href="#">关于我们</a>
              </dt>
              <dd>
                <a href="#">我的品牌</a>
              </dd>
              <dd>
                <a href="#">公司动态</a>
              </dd>
              <dd>
                <a href="#">经历发展</a>
              </dd>
              <dd>
                <a href="#">商品推广</a>
              </dd>
            </dl>
            <dl>
              <dt>
                <a href="#">关于我们</a>
              </dt>
              <dd>
                <a href="#">我的品牌</a>
              </dd>
              <dd>
                <a href="#">公司动态</a>
              </dd>
              <dd>
                <a href="#">经历发展</a>
              </dd>
              <dd>
                <a href="#">商品推广</a>
              </dd>
            </dl>
          </div>
          <div class="ewm">
            <p class="wx">
              <img src="@/assets/Home/images/img71.png" alt />
              <span>微信公众号</span>
            </p>
            <p class="wb">
              <img src="@/assets/Home/images/img72.png" alt />
              <span>微博公众号</span>
            </p>
          </div>
        </div>
      </div>
      <div class="footer_bar">
        <div class="footer_bar_c inner_c">
          <div class="pay">
            <p class="copy">2019 © youhaosuda.com</p>
            <p class="ico">
              <a href="#">
                <img src="@/assets/Home/images/img81.png" alt />
              </a>
              <a href="#">
                <img src="@/assets/Home/images/img82.png" alt />
              </a>
              <a href="#">
                <img src="@/assets/Home/images/img83.png" alt />
              </a>
              <a href="#">
                <img src="@/assets/Home/images/img84.png" alt />
              </a>
              <a href="#">
                <img src="@/assets/Home/images/img85.png" alt />
              </a>
              <a href="#">
                <img src="@/assets/Home/images/img86.png" alt />
              </a>
              <a href="#">
                <img src="@/assets/Home/images/img87.png" alt />
              </a>
            </p>
          </div>
          <div class="super">
            <a href="#" class="pic1"></a>
            <a href="#" class="pic2"></a>
            <a href="#" class="pic3"></a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "@/components/Header.vue";
export default {
  components:{
    Header
  },
  data() {
    return {
      tableData: [{ index: 0 }, { index: 1 }, { index: 2 }],
      multipleSelection: [],
      goodsList: [
        {
          url: require("@/assets/Home/images/png9.png"),
          name: "夹子",
          count: 1,
          price: 78,
          selected: false,
        },
        {
          url: require("@/assets/Home/images/png10.png"),
          name: "勺子",
          count: 1,
          price: 20,
          selected: false,
        },
        {
          url: require("@/assets/Home/images/png15.png"),
          name: "计算器",
          count: 1,
          price: 200,
          selected: false,
        },
      ],
      selected: 0,
      allTotal: 0,
    };
  },
  computed: {},
  watch: {
    multipleSelection(val) {
        this.allTotal = 0;
      this.multipleSelection.forEach(item => {
          this.allTotal += this.goodsList[item.index].count * this.goodsList[item.index].price;
      })
    },
  },
  methods: {
    delAll() {
      if (this.multipleSelection.length > 0) {
        this.multipleSelection.forEach((item) => {
          this.goodsList.splice(item.index, 1);
          this.tableData.pop();
        });
      }
    },
    del(index) {
      this.goodsList.splice(index, 1);
      this.tableData.pop();
    },
    addCount(index) {
      this.goodsList[index].count += 1;
      this.allTotal = 0;
      this.multipleSelection.forEach(item => {
          this.allTotal += this.goodsList[item.index].count * this.goodsList[item.index].price;
      })
    },
    subCount(index) {
      this.goodsList[index].count -= 1;
      this.allTotal = 0;
      this.multipleSelection.forEach(item => {
          this.allTotal += this.goodsList[item.index].count * this.goodsList[item.index].price;
      })
    },
    toggleSelection(rows) {
      if (rows) {
        rows.forEach((row) => {
          this.$refs.multipleTable.toggleRowSelection(row);
        });
      } else {
        this.$refs.multipleTable.clearSelection();
      }
    },
    handleSelectionChange(val) {
      this.multipleSelection = val;
      this.selected = this.multipleSelection.length;
    },
    
  },
};
</script>

<style scoped>
@import "../assets/Home/css/reset.css";
@import "../assets/Home/css/index.css";

td > .cell {
  text-align: center;
  line-height: 80px;
}
.del:hover {
  cursor: pointer;
}
.link {
  cursor: pointer;
}
.cart-content {
  background: #f2f2f2;
}
.main {
  padding-top: 100px;
  width: 74%;
  margin-left: 13%;
}
.cart-title {
  font-size: 32px;
  font-weight: 400;
}
.el-table {
  margin-top: 30px;
}
</style>
