<template>
  <div class="bottom">
    <el-row class="footer">
      <!-- <div>
        <ul>
          <li class="footerTitle">友情链接</li>
          <li>
            <ul class="footerCon">
              <li>
                <a href="https://wjl.cc" target="_blank">无极链官网</a>
              </li>
              <li>
                <a href="https://web3.foundation/" target="_blank">web3.0基金会官网</a>
              </li>
              <li>
                <a href="https://www.chainnews.com" target="_blank">链 闻</a>
              </li>
            </ul>
          </li>
        </ul>
      </div>
      <div>
        <ul>
          <li class="footerTitle">条款说明</li>
          <li>
            <ul class="footerCon">
              <li>
                <a href="/static/file/user_terms.pdf" target="_blank">用户条款</a>
              </li>
              <li>
                <a href="/static/file/privacy_agreement.pdf" target="_blank">隐私条款</a>
              </li>
              <li>
                <a href="/static/file/legal_Notices.pdf" target="_blank">法律声明</a>
              </li>
            </ul>
          </li>
        </ul>
      </div>
      <div>
        <ul>
          <li class="footerTitle">支持</li>
          <li>
            <ul class="footerCon">
              <li>
                <router-link to="/aboutUs">关于我们</router-link>
              </li>
            </ul>
          </li>
        </ul>
      </div>-->
      <el-col :span="18">
        <div class="btmLogo">
          <img src="/static/image/btmLogo.png" alt />
          168Node
        </div>
        <div class="btmList">
          <div>友情链接</div>
          <ul>
            <li>
              <a href="https://wjl.cc/" target="_blank">无极链科技</a>
            </li>
            <li>
              <a href="https://polkadot.network/" target="_blank">Polkadot</a>
            </li>
            <li>
              <a href="https://crust.network/" target="_blank">Crust官网</a>
            </li>
            <li>
              <a href="https://phala.network/zh" target="_blank">Phala官网</a>
            </li>
          </ul>
        </div>
        <div class="btmList clause">
          <div>条款说明</div>
          <ul>
            <li>
              <a href="/static/file/user_terms.pdf" target="_blank">用户条款</a>
            </li>
            <li>
              <a href="/static/file/privacy_agreement.pdf" target="_blank">隐私条款</a>
            </li>
            <li>
              <a href="/static/file/legal_Notices.pdf" target="_blank">法律声明</a>
            </li>
          </ul>
        </div>
      </el-col>
      <el-col :span="6" class="WeChatQrCode">
        <div>
          <img src="/static/image/officailAccount.jpg" width="124px" />
          <div class="WeChatQrCodeName">公众号</div>
        </div>
        <div>
          <img src="/static/image/poolUser.png" width="124px" />
          <div class="WeChatQrCodeName">微信客服</div>
        </div>
      </el-col>
    </el-row>
    <div id="cnzz_box" class="center">
      <span id="cnzz_stat_icon_1278912268"></span>
    </div>
  </div>
</template>

<script>
export default {
  name: "navBottom",
  created() {
    let script = document.createElement("script");
    script.type = "text/javascript";
    script.src = "https://s9.cnzz.com/z_stat.php?id=1278912268&show=pic";
    document.body.appendChild(script);
  }
};
</script>
<style scoped>
.bottom {
  background: #20252e;
  background-size: 100% 100%;
}
.footer {
  width: 1200px;
  margin: 0 auto;
  box-sizing: border-box;
  /* color: rgba(72, 69, 68, 1);
  display: flex;
  justify-content: space-between; */
  padding: 36px 0;
}
.footerTitle {
  font-size: 16px;
  margin-bottom: 36px;
}
.footerCon li {
  margin-bottom: 13px;
}
.footerCon li a {
  color: rgba(72, 69, 68, 1);
  font-size: 14px;
}
.btmLogo {
  display: flex;
  align-items: flex-end;
  font-size: 23px;
  padding: 6px 0;
  border-bottom: 1px solid #3b3e45;
}
.btmList {
  margin-top: 21px;
  display: flex;
  align-items: center;
}
.btmList div {
  margin-right: 24px;
  font-size: 17px;
  font-weight: bolder;
}
.btmList ul {
  display: flex;
}
.btmList ul li {
  margin-right: 38px;
}
.btmList ul li a {
  color: #afb1b4;
  font-size: 14px;
  line-height: 14px;
}
.clause ul li {
  margin-right: 46px;
}
.WeChatQrCode {
  display: flex;
  padding-left: 30px;
  text-align: center;
  color: rgba(255, 255, 255, 0.7);
  font-size: 12px;
}
.WeChatQrCode > div:first-child {
  margin-right: 68px;
}
.WeChatQrCode .WeChatQrCodeName {
  margin-top: 20px;
}
</style>
