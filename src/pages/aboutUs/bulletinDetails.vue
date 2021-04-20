<template>
  <div class="bulletinDetails">
    <div class="goBullet">
      <router-link to="/bulletin">&lt; 返回公告</router-link>
    </div>
    <div class="infoItem">
      <div class="noticeTitle center">
        {{noticeData.title}}
        <div class="noticeDate">{{noticeData.createDate|datetimeparse('YYYY-MM-dd')}}</div>
      </div>
      <div class="noticeCon" v-html="noticeData.content"></div>
      <div class="noticeUser">
        <p>168矿池</p>
        <p class="noticeDate">{{noticeData.createDate|datetimeparse('YYYY-MM-dd')}}</p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "bulletinDetails",
  data() {
    return {
      noticeData: ""
    };
  },
  methods: {
    // 公告
    getNotice() {
      this.$api
        .getNoticeCon({ id: this.$Base64.decode(this.$route.params.id) })
        .then(res => {
          this.noticeData = res.data[0];
          console.log(res);
        });
    }
  },
  mounted() {
    this.getNotice();
  }
};
</script>
<style scoped>
.bulletinDetails {
  width: 1000px;
  margin: 15px auto 53px auto;
  /* box-shadow: 0px 0px 20px rgba(73, 150, 255, 0.1); */
  background: #252b35;
}
.goBullet {
  width: 1000px;
  padding: 30px 80px 87px 80px;
}
.goBullet a {
  color: rgba(189, 189, 189, 1);
}
.infoItem {
  width: 800px;
  margin: 0 auto;
  min-height: 500px;
}
.noticeTitle {
  padding-bottom: 30px;
  font-weight: bold;
  border-bottom: 1px solid rgba(230, 230, 230, 1);
  font-size: 18px;
}
.noticeCon {
  padding-top: 34px;
}
.noticeDate {
  margin-top: 10px;
  color: #999999;
  font-size: 14px;
}
.noticeUser {
  padding-top: 10px;
  color: #999999;
}
.noticeUser p {
  font-size: 14px;
  text-align: right;
}
</style>

