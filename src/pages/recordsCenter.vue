<template>
  <div>
    <div class="dataCon">
      <ul class="dataMask">
        <li class="dataItem" v-for="(item, index) in aboutUsData" :key="index">
          <div>{{ item.title }}</div>
          <div>{{ item.text }}</div>
        </li>
      </ul>
    </div>
    <div class="records">
      <div class="recordsCon">
        <div class="recordsConLeft">
          <div class="title">UPS配电系统</div>
          <p class="contents">
            系统结构保障机架供电可靠性
            <br />单组UPS采用（N+1）冗余备份
            <br />满负荷情况下 可支持30分钟以上
            <br />单台UPS由400KVA的UPS主机及4组电池组成
          </p>
        </div>
        <div class="recordsConRight">
          <div>
            <div class="title">柴油发电系统</div>
            <p class="contents">
              单台功率 2000KVA
              <br />配备一个 15吨 的地下油库
              <br />可供三台柴油机发电机组 16小时 满负荷运行
            </p>
          </div>
          <div>
            <div class="title">安保监控系统</div>
            <p class="contents">
              门禁管制，视频监控，防盗报警
              <br />烟感、温感、消防报警，24小时连线监控，保障机房设备的安全
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "recordsCenter",
  data() {
    return {
      aboutUsData: [
        {
          title: "1.稳定可靠",
          text: "T3级别五星级IDC机房，确保矩阵专机稳定运行"
        },
        {
          title: "2.降低成本",
          text: "轻松托管费用低廉，免除额外的维护费用"
        },
        {
          title: "3.安全放心",
          text: "专业化数据中心运维管理系统，现场7x24小时响应问题解决"
        },
        {
          title: "4.团队专业",
          text: "强运维团队拥有大规模服务器运维经验"
        }
      ]
    };
  }
};
</script>
<style scoped>
p {
  margin: 0;
  padding: 0;
  line-height: 32px;
  color: #d5d5d5;
}
.records {
  padding: 140px 0 208px 0;
  text-align: center;
  background: linear-gradient(to right, #1e232e, #292e38);
}
.recordsCon {
  width: 1200px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
}
.recordsCon > div {
  width: 585px;
  height: 630px;
}
.recordsConLeft {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background: url("/static/image/recordsPus.png") no-repeat;
  border: 2px solid transparent;
}
.recordsConLeft:hover {
  border: 2px solid #0e5ea6;
}
.recordsConLeft .contents {
  margin-top: 20px;
}
.title {
  font-size: 30px;
  font-weight: bolder;
}
.contents {
  font-size: 18px;
  margin-top: 10px;
}
.recordsConRight {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.recordsConRight > div {
  height: 300px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  box-sizing: border-box;
  border: 2px solid transparent;
}
.recordsConRight > div:hover {
  border-color: #0e5ea6;
}
.recordsConRight > div:nth-of-type(1) {
  background: url("/static/image/recordsR_top.png") no-repeat;
}
.recordsConRight > div:nth-of-type(2) {
  background: url("/static/image/recordsR_btm.png") no-repeat;
  background-position-y: -1px;
}
</style>