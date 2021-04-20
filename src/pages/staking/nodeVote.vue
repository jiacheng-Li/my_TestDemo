<template>
  <div class="voteDetails">
    <div class="nodeInfo">
      <!-- <el-col :span="7">
        <div class="nodeSign">
          <img src="/static/image/node2.png" height="210" />
        </div>
      </el-col>-->
      <div>
        <!-- logo+下拉 -->
        <div class="voteSelect">
          <img :src="nodeInfo.logo" width="45" />
          <el-select
            v-model="selectValue"
            placeholder="请选择"
            size="mini"
            @change="nodeChange"
            style="width:118px;margin-left:10px"
          >
            <el-option
              v-for="item in options"
              :key="item.id"
              :label="item.name"
              :value="item.id"
              v-show="item.isOnline"
            ></el-option>
          </el-select>
        </div>
        <div class="nodeVerifi">
          <span>节点名称：</span>
          <span>{{nodeInfo.nodeName || '--'}}</span>
        </div>
        <div class="nodeAddr">
          <span>节点地址：{{nodeInfo.nodeAddress}}</span>
          <div class="qrHover">
            <img src="/static/image/qrImg.png" />
            <div id="qrcode" class="qrImgHover"></div>
          </div>
          <button
            type="button"
            class="bgBtn"
            v-clipboard:copy="nodeInfo.nodeAddress"
            v-clipboard:success="copySuccess"
          >复制地址</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import QRCode from "qrcodejs2";
import nodeInfo from "@/assets/localData/nodeInfo";
import filter from "../../utils/filter";
export default {
  name: "chainxVote",
  data() {
    return {
      options: nodeInfo.nodeData,
      selectValue: "",
      nodeInfo: {}
    };
  },
  methods: {
    copySuccess(e) {
      this.$message("复制成功");
    },
    getQrcode() {
      this.$nextTick(() => {
        document.getElementById("qrcode").innerHTML = "";
        let qrcode = new QRCode("qrcode", {
          width: 130,
          height: 130,
          text: this.nodeInfo.nodeAddress,
          colorDark: "#000",
          colorLight: "#fff"
        });
      });
    },
    // 节点数据
    getNodeData(id) {
      this.nodeInfo = nodeInfo.nodeData.find(x => {
        console.log(x);
        return x.id === id;
      });
      this.nodeInfo == null && this.$router.push({ path: "/" });
      this.getQrcode();
    },
    // 币种切换
    nodeChange(val) {
      this.getNodeData(val);
    },
    // 获取币种
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
<style  scoped>
.voteDetails {
  padding: 100px 0;
  /* background: url("/static/image/bg4.png") no-repeat; */
  background-position: left bottom;
  background-size: cover;
  min-height: 55vh;
}
.nodeInfo {
  width: 1400px;
  margin: 40px auto 30px auto;
  /* background: rgba(255, 255, 255, 1); */
  background: linear-gradient(to right, #262b34, #1a202b);
  /* box-shadow: 0px 9px 14px rgba(73, 150, 255, 0.1); */
  padding: 65px 0;
  box-sizing: border-box;
  border-bottom-right-radius: 5px;
  border-bottom-left-radius: 5px;
  border: 1px solid #252a33;
  position: relative;
}
.nodeInfo::after {
  content: "";
  width: 1400px;
  height: 10px;
  position: absolute;
  background: linear-gradient(to right, #1587ed, #3dd399);
  top: -10px;
  left: -1px;
}
.voteSelect {
  position: absolute;
  top: 0;
  left: -70px;
  width: 505px;
  height: 98px;
  background: linear-gradient(to right, #323844, #222832);
  transform: translateY(-60px);
  z-index: 99;
  border-radius: 0 50px 50px 0;
  display: flex;
  justify-content: center;
  align-items: center;
  border: 1px solid #393f4a;
}
.voteSelect::after {
  content: "";
  width: 73px;
  height: 1px;
  position: absolute;
  left: -2px;
  bottom: -14px;
  background: #fdfdfd;
  transform: rotate(21deg) scaleY(0.2);
}
.voteSelect img {
  display: block;
  width: 71px;
}
.voteSelect /deep/ .el-select {
  width: 165px !important;
}
.voteSelect /deep/ .el-input__inner {
  border: transparent;
  font-size: 26px;
  color: #ffffff;
}
.voteSelect /deep/ .el-select .el-input .el-select__caret {
  font-size: 20px;
  font-weight: bolder;
  color: #ffffff;
}
.nodeSign {
  position: relative;
  width: 100%;
  height: 170px;
}
.nodeSign img {
  position: absolute;
  left: 0;
  bottom: 0;
}
.nodeVerifi {
  padding-left: 145px;
  background: linear-gradient(to right, #232832, #303743);
}
.nodeVerifi span {
  line-height: 84px;
  font-size: 22px;
}
/* .nodeVerifi span:last-child {
  color: rgba(0, 100, 251, 1);
} */
.nodeAddr {
  padding-left: 145px;
}
.nodeAddr img {
  vertical-align: middle;
}
.nodeAddr span {
  line-height: 84px;
  font-size: 22px;
}
.qrHover {
  display: inline-block;
  position: relative;
  margin: 0 20px 0 25px;
}
.qrImgHover {
  position: absolute;
  top: 30px;
  left: 50%;
  transform: translateX(-50%);
  -webkit-transform: translateX(-50%);
  -ms-transform: translateX(-50%);
  -moz-transform: translateX(-50%);
  -o-transform: translateX(-50%);
  display: none;
  padding: 10px;
  background: rgba(255, 255, 255, 1);
  box-shadow: 0px 5px 20px rgba(125, 142, 188, 1);
}
.qrHover:hover {
  cursor: pointer;
}
.qrHover:hover .qrImgHover {
  display: block;
}
</style>
