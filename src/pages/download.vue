<template>
  <div class="download">
    <div class="WeChatMask" v-show="isWeChat">
      <div class="WeChatTips">“ 点击右上角选择在浏览器中打开 ”</div>
      <img src="/static/image/WeChat1.png" class="WeChat1" />
      <img src="/static/image/WeChat2.png" class="WeChat2" />
    </div>
    <div>
      <a
        href="https://mxcapp.oss-cn-shenzhen.aliyuncs.com/mxc.apk"
        download="https://mxcapp.oss-cn-shenzhen.aliyuncs.com/mxc.apk"
        class="appDownLoad"
      >Android下载</a>
    </div>
  </div>
</template>

<script>
export default {
  name: "download",
  data() {
    return {
      isWeChat: false
    };
  },
  methods: {
    getAuthority() {
      if (/Android|webOS|iPhone|iPod|BlackBerry/i.test(navigator.userAgent)) {
        console.log("现在移动端打开的");
      } else {
        this.$router.push({ path: "/" });
      }
      var wx = (function() {
        return (
          navigator.userAgent.toLowerCase().indexOf("micromessenger") !== -1
        );
      })();
      if (wx) {
        this.isWeChat = true;
      }
      let meta = document.querySelector('meta[name="viewport"]');
      meta.content =
        "width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no,viewport-fit=cover";
      document.title = "168Node APP DOWNLOAD";
    },
    appDownload() {
      window.open("");
    }
  },
  mounted() {
    this.getAuthority();
  }
};
</script>
<style  scoped>
.download {
  background: url("/static/image/appDownloadBg.png") no-repeat center center;
  background-size: cover;
  width: 100vw;
  height: 100vh;
  position: relative;
}

.WeChatMask {
  width: 100vw;
  height: 100vh;
  z-index: 10000;
  background-color: rgba(0, 0, 0, 0.6);
  color: rgba(254, 252, 252, 1);
  font-size: 4.3vw;
  text-align: center;
  position: fixed;
}
.WeChatTips {
  position: absolute;
  top: 35vh;
  right: 10vw;
}
.WeChat1 {
  position: absolute;
  top: 7vh;
  right: 10vw;
  width: 30vw;
  height: 27vh;
}
.WeChat2 {
  position: absolute;
  top: 2vh;
  right: 5vw;
  width: 10vw;
  height: 8vh;
}
.appDownLoad {
  display: block;
  width: 65vw;
  line-height: 11vw;
  margin: 0 auto;
  text-align: center;
  background: transparent;
  color: rgba(254, 252, 252, 1);
  box-shadow: 0 0 5px rgba(19, 47, 142, 1);
  border-radius: 18px;
  font-size: 4.3vw;
  position: absolute;
  left: 50%;
  bottom: 20%;
  transform: translate(-50%, -20%);
}
</style>
