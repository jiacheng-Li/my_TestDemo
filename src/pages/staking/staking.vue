<template>
  <section class="nodeData">
    <!-- <div class="blockTitle partnersBG">Staking</div> -->
    <div class="nodeInfo">
      <div class="stakingBanner">
        <div class="stakingIntroduction">
          <div>
            <img src="/static/image/recommend_1.png" />
          </div>
          <div class="stakingText">
            <p>168Node 深度参与公链生态建设，成为各公链的超级节点，提供节点基础设施与服务。</p>
            <p>您只需将拥有的票权抵押给验证人 168Node，即可获取 Staking 收益。</p>
          </div>
        </div>
      </div>
      <div class="nodeDataConBg">
        <div class="nodeDataCon">
          <div v-for="(item,index) in nodeData" :key="index" class="nodeItemBg">
            <div class="nodeItem">
              <img :src="item.logo" width="47px" />
              <div class="nodeName">{{item.name}}</div>
              <div class="nodeDigital">
                <div>
                  <div v-show="item.isOnline">预计年化收益率</div>
                  <p>{{item.annualizedRate}}</p>
                </div>
                <div v-show="item.handlingFee !=''">
                  <div>手续费</div>
                  <p>{{ item.handlingFee}}</p>
                </div>
              </div>
              <div class="nodeMore">
                <router-link
                  :to="'/nodeVote/'+item.id"
                  class="roundBtn rimBtn roundBtnHover"
                  v-show="item.isOnline"
                >投票</router-link>
                <a
                  class="roundBtn rimBtn roundBtnHover"
                  :href="item.voteAddress"
                  v-if="item.voteAddress?true:false"
                  target="_blank"
                >投票</a>
                <a :href="item.website" class="roundBtn rimBtn roundBtnHover" target="_blank">了解更多</a>
              </div>
            </div>
          </div>
        </div>
      </div>
      <section class="advantage center">
        <div class="partTitle">代建节点</div>
        <div class="advantageCon">
          <div class="advantageItems">
            <div :span="8" v-for="(item,index) in advantage" :key="index" class="advantageItem">
              <img :src="item.img" height="100" />
              <p class="advantageTitle">{{item.title}}</p>
              <p>{{item.con}}</p>
            </div>
          </div>
        </div>
      </section>
      <section class="support">
        <div class="supportTitle">支持的项目</div>
        <div class="supportProject">
          <div class="supportProjectItem">
            <div v-for="(item,index) in nodeDatas" :key="index" class="center">
              <img :src="item.logo" width="80" />
            </div>
          </div>
        </div>
      </section>
      <div class="inquiry">
        <div class="idcBtn">
          <div class="idcBtn_sty">
            <button type="button" class="moreBtn">立即咨询</button>
          </div>
        </div>
        <div class="inquiryCode">
          <div>
            <img src="/static/image/officailAccount.jpg" width="124px" />
            <div class="WeChatQrCodeName">公众号</div>
          </div>
          <div>
            <img src="/static/image/poolUser.png" width="124px" />
            <div class="WeChatQrCodeName">微信客服</div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import nodeInfo from "@/assets/localData/nodeInfo";
export default {
  name: "home",
  data() {
    return {
      nodeData: nodeInfo.nodeData,
      advantage: [
        {
          img: "/static/image/advantage1.png",
          title: "专业团队",
          con: "团队拥有丰富搭建节点经验"
        },
        {
          img: "/static/image/advantage2.png",
          title: "价格从优",
          con: "价格透明，量大从优"
        },
        {
          img: "/static/image/advantage3.png",
          title: "专人服务",
          con: "7*24小时，一对一服务"
        }
      ],
      nodeDatas: [
        {
          logo: "/static/image/ETH.png",
          symbol: "ETH 2.0"
        },
        {
          logo: "/static/image/DOT.png",
          symbol: "DOT"
        },
        {
          logo: "/static/image/KSM.png",
          symbol: "Kusama"
        },
        {
          logo: "/static/image/PCX.png",
          symbol: "PCX"
        },
        {
          logo: "/static/image/ring.png",
          symbol: "Ring"
        }
      ]
    };
  }
};
</script>
<style  scoped>
/* .nodeData {
  margin: 70px 0 100px 0;
} */
.stakingBanner {
  width: 100%;
  height: 700px;
  /* background: url("/static/image/staking_banner.png") no-repeat; */
}
.stakingBanner::after {
  content: "";
  width: 100%;
  height: 100%;
  background: url("/static/image/staking_banner.png") no-repeat;
  background-size: 2134px;
  opacity: 0.3;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  position: absolute;
  z-index: -1;
}
.stakingIntroduction {
  width: 1200px;
  height: 100%;
  margin: 0 auto;
  display: flex;
  align-items: center;
  color: #ffffff;
  text-align: center;
}
.stakingIntroduction img {
  margin-bottom: -300px;
}
.stakingText {
  /* border-bottom: 3px solid #ffffff; */

  /* -webkit-border-bottom: 3px solid #ffffff; */
  border-bottom-width: 3px;
  border-bottom-style: solid;
  border-bottom-color: #fff;
  border-top-width: 0px;
  border-left-width: 0px;
  border-right-width: 0px;
  border-image: linear-gradient(to right, #1587ed, #3dd399) 20 20;
}
.stakingText p {
  font-size: 20px;
  line-height: 40px;
  white-space: nowrap;
}
.nodeDataConBg {
  height: 556px;
  background: linear-gradient(to right, #1a202b, #292e38);
  display: flex;
  align-items: flex-end;
  justify-content: center;
}

/* .nodeInfo {
  background: linear-gradient(
    to top,
    transparent 0%,
    transparent 25%,
    rgba(245, 249, 255, 1) 26%,
    rgba(245, 249, 255, 1) 100%
  );
} */
.partTitle {
  color: #ffffff;
  font-size: 35px;
  font-weight: bolder;
  text-align: center;
  height: 100px;
  line-height: 100px;
  font-size: 36px;
  position: relative;
}
.supportTitle {
  color: #ffffff;
  font-size: 35px;
  font-weight: bolder;
  text-align: center;
  height: 100px;
  line-height: 100px;
  font-size: 36px;
  position: relative;
}

.advantage {
  padding-top: 230px;
}
.advantageCon {
  width: 100%;
  background: linear-gradient(to right, #292e38, #1a202b);
}
.advantageItems {
  width: 1200px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
}
.advantageItem {
  width: 33.31%;
  height: 294px;
  padding: 46px 0;
  box-sizing: border-box;
  border-radius: 20px;
  color: #ffffff;
  transition: all 0.3s;
}
.advantageItem:hover {
  background: #292e38;
}
.advantageItem p {
  margin: 0;
}
.advantageItem .advantageTitle {
  font-weight: bold;
  font-size: 22px;
  line-height: 32px;
  margin-top: 28px;
  margin-bottom: 8px;
}
.support {
  padding-top: 35px;
  width: 100%;
}
.supportProject {
  width: 100%;
  background: linear-gradient(to right, #292e38, #1a202b);
  padding: 16px 0;
}
.supportProjectItem {
  width: 700px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
}
.supportProjectName {
  font-size: 18px;
  color: rgba(22, 53, 135, 1);
  margin-top: 20px;
}
.inquiry {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 120px;
}
.inquiry .idcBtn {
  width: 170px;
  font-size: 20px;
}
.inquiry .idcBtn .moreBtn {
  padding: 20px 39px;
}
.idcBtn:hover .moreBtn {
  background: transparent;
}
.idcBtn:hover + .inquiryCode {
  opacity: 1;
}
.inquiryCode {
  margin: 0 auto;
  width: 455px;
  box-sizing: border-box;
  padding: 32px 85px;
  display: flex;
  justify-content: space-between;
  text-align: center;
  color: rgba(245, 245, 245, 0.8);
  background: #20252e;
  margin-bottom: 30px;
  opacity: 0;
  border-radius: 5px;
  transition: all 0.2s;
}
.WeChatQrCodeName {
  font-size: 14px;
  margin-top: 8px;
}
</style>
