<template>
  <div class="construction">
    <div class="constructionTop">
      <div class="constructionCon">
        <img class="topImg" src="/static/image/appTop.png" alt />
        <div class="constructionTop-right">
          <!-- 下载按钮 -->
          <!-- <div class="rightBtn">
            <div class="idcBtn">
              <div class="idcBtn_sty">
                <button
                  type="button"
                  router-link
                  @click="$router.push('/construction')"
                  class="moreBtn"
                >ios下载</button>
              </div>
            </div>
            <div class="idcBtn">
              <div class="idcBtn_sty">
                <button
                  type="button"
                  router-link
                  @click="$router.push('/construction')"
                  class="moreBtn"
                >安卓下载</button>
              </div>
            </div>
          </div>-->
          <p class="rightText">
            支持Crsut/Phala等币种的挖矿、矿机管理、收益查询
            <br />挖矿数据实时显示，流畅的使用体验
          </p>
          <img class="handLogo" src="/static/image/appTop_hand.png" alt />
          <img class="topTitle" src="/static/image/appTop_title.png" alt />
        </div>
      </div>
    </div>
    <div class="appDetailed">
      <div class="conBanner">
        <div class="appDetailed-item">
          <div class="appDetailed-title">区块浏览器</div>
          <p>为用户提供详细的全网信息、全网算力、节点排行榜</p>
        </div>
        <div class="appDetailed-item">
          <div class="appDetailed-title">矿池</div>
          <p>
            机器远程接入，汇集分散算力，提升挖矿收益
            <br />算力占比、贡献度、账户数据实时查阅，收益明细一目了然
          </p>
        </div>
        <div class="appDetailed-item">
          <div class="appDetailed-title">矿机管理</div>
          <p>矿机多维数据实时监控、矿机离线及时推送、智能排序便捷管理</p>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "construction",
  data() {
    return {};
  }
};
</script>
<style  scoped>
.constructionTop {
  padding: 118px 0 140px 0;
}
.constructionCon {
  margin: 0 auto;
  width: 1200px;
  display: flex;
}
.topImg {
  display: block;
  width: 519px;
}
.constructionTop-right {
  /* background: #fff; */
  padding-left: 20px;
  padding-bottom: 60px;
  flex-grow: 1;
  /* margin-bottom: -28px; */
  display: flex;
  flex-direction: column-reverse;
}
.rightBtn {
  display: flex;
}
.rightBtn > div:nth-of-type(1) {
  margin-right: 28px;
}
.constructionTop .idcBtn_sty {
  background: #fff;
  margin-top: 0;
}
.constructionTop .moreBtn {
  font-size: 18px;
  padding: 16px 30px;
}
.rightText {
  font-size: 24px;
  line-height: 51px;
}
.handLogo {
  display: block;
  width: 40px;
  height: 50px;
  margin-bottom: -25px;
}
.topTitle {
  display: block;
  width: 426px;
  height: 52px;
  margin-bottom: 10px;
}
.appDetailed {
  padding: 76px 0 159px 0;
  background: linear-gradient(to right, #292e38, #1b212c);
}
.conBanner {
  width: 1200px;
  height: 1500px;
  margin: 0 auto;
  background: url("/static/image/appContentImg.png") no-repeat center top;
}
.appDetailed-item {
  height: 33.3%;
  box-sizing: border-box;
}
.appDetailed-title {
  font-size: 35px;
}
.appDetailed-item p {
  font-size: 22px;
  margin-top: 20px;
  padding-left: 14px;
  line-height: 40px;
}
.appDetailed-item:nth-of-type(1) {
  width: 610px;
  padding-top: 215px;
  padding-left: 90px;
  text-align: right;
}
.appDetailed-item:nth-of-type(2) {
  padding-top: 305px;
  padding-left: 585px;
}
.appDetailed-item:nth-of-type(3) {
  width: 790px;
  padding-top: 365px;
  padding-left: 140px;
  text-align: center;
}
.appDetailed-item:nth-of-type(1) .idcBtn_sty::after {
  content: url("/static/image/appDetailed_hand.png");
  position: absolute;
  top: 42px;
  right: -62px;
}
.appDetailed-item:nth-of-type(2) .idcBtn_sty::after {
  content: url("/static/image/appDetailed_hand.png");
  position: absolute;
  top: 22px;
  left: -72px;
}
.appDetailed-item:nth-of-type(3) .idcBtn_sty::after {
  content: url("/static/image/appDetailed_hand.png");
  position: absolute;
  top: 4px;
  right: -98px;
}
</style>
