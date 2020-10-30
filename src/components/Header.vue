<template>
  <div class="header">
    <div class="header_c inner_c">
      <h1 class="logo">青竹商城</h1>
      <dl class="allType">
        <dt>
          <a href="#">查看所有类型</a>
        </dt>
        <dd>
          <div class="dd_inn">
            <ul class="dd_cont">
              <li>
                <a href="#">不锈钢</a>
              </li>
              <li>
                <a href="#">原料水泥</a>
              </li>
              <li>
                <a href="#">塑料</a>
              </li>
              <li>
                <a href="#">木质</a>
              </li>
              <li>
                <a href="#">陶瓷</a>
              </li>
            </ul>
            <ul class="pro">
              <li>
                <a href="#">
                  <div class="pic">
                    <img src="@/assets/Home/images/img25.png" alt />
                  </div>
                  <div class="content">
                    <h3>简约木质餐盘</h3>
                    <span>￥200</span>
                  </div>
                </a>
                <div class="mask">
                  <a href="#" class="btn">查看详情</a>
                </div>
              </li>
              <li>
                <a href="#">
                  <div class="pic">
                    <img src="@/assets/Home/images/img26.png" alt />
                  </div>
                  <div class="content">
                    <h3>简约木质餐盘</h3>
                    <span>￥200</span>
                  </div>
                </a>
                <div class="mask">
                  <a href="#" class="btn">查看详情</a>
                </div>
              </li>
              <li>
                <a href="#">
                  <div class="pic">
                    <img src="@/assets/Home/images/img27.png" alt />
                  </div>
                  <div class="content">
                    <h3>简约木质餐盘</h3>
                    <span>￥200</span>
                  </div>
                </a>
                <div class="mask">
                  <a href="#" class="btn">查看详情</a>
                </div>
              </li>
            </ul>
          </div>
        </dd>
      </dl>
      <ul class="nav">
        <li class="link" @click="toIndex">
          <span>首页</span>
        </li>
        <li class="link" @click="toProducts">
          <span>所有产品</span>
        </li>
        <li class="link" @click="toPersonal">
          <span>个人中心</span>
        </li>
      </ul>
      <div class="reg">
        <div class="ico">
          <span class="ico_c link" @click="toCart"></span>

          <div class="settle">
            <p class="con">
              0件商品 共计：
              <span>￥0</span>
            </p>
            <a href="#" class="btn">结算</a>
          </div>
          <span class="con">0</span>
        </div>
        <div class="reg_c">
          <span class="link" id @click="toLogin">登陆</span>
          <span>&nbsp;|&nbsp;</span>
          <span class="link" @click="toRegister">注册</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    toLogin() {
      this.$router.push({
        path: "/login"
      });
    },
    toRegister() {
      this.$router.push({
        path: "/register"
      });
    },
    toBlog() {
      this.$router.push({
        path: "/blog"
      });
    },
    toProducts() {
      this.$router.push({
        path: "/allproducts"
      });
    },
    toIndex() {
      this.$router.push({
        path: "/"
      });
    },
    toArticle() {
      this.$router.push({
        path: "/article"
      });
    },
    toPersonal() {
      this.$router.push({
        path: "/personal"
      });
    },
    toCart() {
      this.$router.push({
        path: "/cart"
      });
    }
  }
};
</script>

<style>
</style>