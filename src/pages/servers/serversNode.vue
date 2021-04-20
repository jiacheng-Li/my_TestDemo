<template>
  <div class="serversNode">
    <div class="nodeitem">
      <div class="voteSelect">
        <p>{{ nodeInfo.productModel }}</p>
      </div>
      <div class="nodeitemCon">
        <div class="nodeitemMsg">
          <div>
            CPU:
            <b>{{ nodeInfo.cpu }}</b>
          </div>
          <div>
            存储空间:
            <b>{{ nodeInfo.rom }}</b>
          </div>
          <div>
            适用算法:
            <b>{{ nodeInfo.algorithm }}</b>
          </div>
          <div>
            <!-- <router-link :to="'/serversNode/' + nodeInfo.id" class="miningBtn">查看详情</router-link> -->
          </div>
        </div>
        <div class="nodeitemMsg">
          <img class="nodeitemImg" :src="nodeInfo.image" alt />
        </div>
      </div>
    </div>
    <div class="nodeMsg">
      <div class="serversNodeBtn">
        <div class="idcBtn">
          <div class="idcBtn_sty">
            <button
              type="button"
              router-link
              @click="$router.push('/serversNode/' + nodeInfo.id)"
              class="moreBtn"
            >参数配置</button>
          </div>
        </div>
      </div>
      <div class="serversText">
        <ul>
          <li>
            产品型号：
            <b>{{ nodeInfo.productModel }}</b>
          </li>
          <li>
            主板：
            <b>{{ nodeInfo.mainboard }}</b>
          </li>
          <li>
            CPU：
            <b>{{ nodeInfo.cpu }}</b>
          </li>
          <li>
            内存：
            <b>{{ nodeInfo.ram }}</b>
          </li>
          <li>
            硬盘：
            <b>{{ nodeInfo.hardDisk }}</b>
          </li>
          <li>
            电源：
            <b>{{ nodeInfo.powerSupply }}</b>
          </li>
          <li>
            SSD：
            <b>{{ nodeInfo.ssd }}</b>
          </li>
          <li>
            阵列卡：
            <b>{{ nodeInfo.raidController }}</b>
          </li>
          <li>
            散热器：
            <b>{{ nodeInfo.heatSink }}</b>
          </li>
          <li>
            机箱：
            <b>{{ nodeInfo.crate }}</b>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>
<script>
import serversMessage from "@/assets/localData/serversMessage";
export default {
  name: "chainxVote",
  data() {
    return {
      options: serversMessage.serversData,
      selectValue: "",
      nodeInfo: {}
    };
  },
  methods: {
    // 服务器数据
    getNodeData(id) {
      this.nodeInfo = serversMessage.serversData.find(x => {
        return x.id === id;
      });
      this.nodeInfo == null && this.$router.push({ path: "/" });
    },
    // nodeChange(val) {
    //   this.getNodeData(val);
    // },
    // 获取服务器id
    getNodeType() {
      this.selectValue = this.$route.params.id;
      this.getNodeData(this.selectValue);
    }
  },
  mounted() {
    this.getNodeType();
  },
  watch: {
    $route(to, from) {
      if (this.$route.params.id) {
        this.getNodeType();
      }
    }
  }
};
</script>

<style scoped>
.nodeitemMsg:nth-of-type(1) {
  box-sizing: border-box;
  padding-top: 100px;
}
.serversNode {
  padding-bottom: 360px;
}
.miningBtn {
  line-height: 60px;
}
.serversNodeBtn {
  padding-top: 80px;
  padding-bottom: 66px;
}
.idcBtn_sty {
  width: 280px;
}
.moreBtn {
  display: block;
  width: 100%;
  padding: 14px 0;
}
.serversText {
  padding: 70px 0;
  background: linear-gradient(to right, #1a202b, #292e38);
}
.serversText ul {
  width: 666px;
  margin: 0 auto;
}
.serversText ul li {
  padding: 23px 0 23px 50px;
  font-size: 22px;
  line-height: 22px;
  display: flex;
  align-items: center;
}
.serversText ul li b {
  font-size: 30px;
  padding-left: 24px;
  line-height: 30px;
}
.serversText ul li:nth-of-type(1) b {
  padding-left: 40px;
}
.serversText ul li:nth-of-type(1) {
  background: linear-gradient(to right, #232832, #292e39);
}
.serversText ul li:nth-of-type(2) {
  background: linear-gradient(to right, #262b35, #262b35);
}
.serversText ul li:nth-of-type(3) {
  background: linear-gradient(to right, #232832, #2b313c);
}
.serversText ul li:nth-of-type(4) {
  background: linear-gradient(to right, #232832, #292f3a);
}
.serversText ul li:nth-of-type(5) {
  background: linear-gradient(to right, #232832, #313844);
}
.serversText ul li:nth-of-type(6) {
  background: linear-gradient(to right, #232832, #282e39);
}
.serversText ul li:nth-of-type(7) {
  background: linear-gradient(to right, #232832, #2e3540);
}
.serversText ul li:nth-of-type(8) {
  background: linear-gradient(to right, #232832, #292f3a);
}
.serversText ul li:nth-of-type(9) {
  background: linear-gradient(to right, #232832, #272d37);
}
.serversText ul li:nth-of-type(10) {
  background: linear-gradient(to right, #232832, #2e3540);
}
</style>