<template>
  <div class="notice">
    <div class="infoItem">
      <div class="noData" v-show="noticeData.length == 0">
        <img src="/static/image/noData.png" />
        <p>暂无数据</p>
      </div>
      <ul>
        <li
          v-for="(item,index) in noticeData"
          :key="index"
          class="noticeItem"
          @click="$router.push({path:'/bulletinDetails/'+$Base64.encode(item.id)})"
        >
          <div class="noticeDate">{{item.createDate|datetimeparse('YYYY-MM-dd')}}</div>
          <div class="noticeTitle">{{item.title}}</div>
          <img src="/static/image/icon_jiantou.png" width="15" class="noticeImg" />
        </li>
      </ul>
      <div class="paging" v-show="total>0">
        <el-pagination
          layout="prev, pager, next"
          :page-count="total"
          @current-change="getNoticeData"
        ></el-pagination>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "bulletin",
  data() {
    return {
      noticeData: [],
      total: 0,
      pageNumber: 1
    };
  },
  methods: {
    // 公告
    getNoticeData(val) {
      var pageNumber = 1;
      if (val !== undefined) pageNumber = val;
      this.$api
        .getNotice({
          page: pageNumber,
          size: 10
        })
        .then(res => {
          this.total = res.page.totalPage;
          this.noticeData = res.data;
          console.log(this.noticeData);
        });
    }
  },
  mounted() {
    this.getNoticeData();
  }
};
</script>
<style scoped>
.notice {
  width: 1000px;
  margin: 60px auto;
}
.infoItem {
  width: 100%;
  margin-top: 60px;
  min-height: 300px;
}
.infoItem .noticeItem:last-child {
  border: none;
}
.noticeItem {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 30px;
  cursor: pointer;
  border-bottom: 1px solid #353a43;
}

.noticeTitle {
  flex: 1;
  position: relative;
  font-size: 16px;
}
.noticeImg {
  display: none;
}
.noticeItem:hover {
  /* box-shadow: 0px 0px 20px rgba(11, 84, 183, 0.1); */
  background: #252b35;
}
.noticeItem:hover .noticeImg {
  display: inline-block;
}
.noticeDate {
  color: rgba(102, 102, 102, 1);
  margin-top: 1px;
  margin-right: 30px;
}
.noticeItem:hover .noticeTitle {
  color: rgba(73, 150, 255, 1);
}
.paging {
  text-align: center;
  margin-top: 20px;
}
</style>

