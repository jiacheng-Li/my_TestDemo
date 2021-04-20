<template>
  <div class="homeInfo">
    <section>
      <el-carousel height="800px" class="banner">
        <el-carousel-item v-for="(item, index) in bannerData" :key="index">
          <img :src="item.imageUrl" height="100%" width="100%" @click="linkTo(item.linkUrl)" />
        </el-carousel-item>
      </el-carousel>
    </section>
    <!-- <section class="bulletin" v-show="noticeData.length !== 0">
      <div>
        <img src="/static/image/icon_bulletin.png" />
        <div class="bulletinCon">
          <div
            class="bulletinItem"
            v-for="(item, index) in noticeData"
            v-if="noticeData[0]"
            :key="index"
            @click="
              $router.push({
                path: '/bulletinDetails/' + $Base64.encode(item.id),
              })
            "
          >
            <span>{{ item.title }}</span>
            <span>{{ item.createDate | datetimeparse("YYYY-MM-dd") }}</span>
          </div>
        </div>
        <router-link to="/bulletin" class="more1">查看更多></router-link>
      </div>
    </section>-->
    <section class="mining">
      <div class="blockTitle produsBg">M384</div>
      <div class="miningItem">
        <el-row>
          <el-col :span="16" class="center">
            <img src="/static/image/168M3.png" />
          </el-col>
          <el-col :span="8" class="miningCon">
            <div>
              <strong>可挖Crust、Phala</strong>稳定、强劲、高效
            </div>
            <div>
              <strong>384TB</strong>储存空间深度定制Linux系统
            </div>
            <div class="mining_sty">
              <button
                type="button"
                router-link
                @click="$router.push('/serversNode/M3168pro')"
                class="miningBtn"
              >查看详情</button>
            </div>
          </el-col>
        </el-row>
      </div>
    </section>
    <section class="idc">
      <div class="blockTitle idcBg">机器托管服务</div>
      <div class="idcBtn">
        <div class="idcBtn_sty">
          <button type="button" router-link @click="$router.push('/staking')" class="moreBtn">查看更多</button>
        </div>
      </div>
      <ul class="idcCon">
        <li class="idcItem" v-for="item in idcData" :key="item.id">
          <div>
            <strong>{{ item.id }}</strong>
            {{ item.title }}
          </div>
          <img :src="item.image" alt />
        </li>
      </ul>
    </section>
    <section class="homeAbout">
      <div class="blockTitle aboutUsBg">全球领先的区块链基础设施综合服务平台</div>
      <div class="dataCon">
        <ul class="dataMask">
          <li class="dataItem" v-for="(item, index) in aboutUsData" :key="index">
            <div>{{ item.title }}</div>
            <div>{{ item.text }}</div>
          </li>
        </ul>
      </div>
    </section>
    <section class="partner">
      <div class="blockTitle partnerBg">合作伙伴</div>
      <div class="partnerMask">
        <!-- <div class="boxs">
          <ul class="partnerCon" @mousedown="move">
            <li class="partnerItem" v-for="(item, index) in partnerData" :key="index">
              <img :src="item.image" alt />
            </li>
          </ul>
        </div>-->
        <div class="swiperMask">
          <div class="swiper-button-prev" slot="button-prev" @click="prev"></div>
          <swiper class="swiper swiper1" ref="mySwiper" :options="swiperOption">
            <swiper-slide class="swiper1Item" v-for="(item, index) in partnerData" :key="index">
              <img :src="item.image" alt />
            </swiper-slide>
            <div class="swiper-pagination" slot="pagination"></div>
          </swiper>
          <div class="swiper-button-next" slot="button-next" @click="next"></div>
        </div>
        <!-- <el-carousel
          indicator-position="none"
          class="partnerLb"
          :autoplay="false"
          type="card"
          height="200px"
        >
          <el-carousel-item
            class="partnerLb-item"
            v-for="(item, index) in partnerData"
            :key="index"
          >
            <img :src="item.image" alt />
          </el-carousel-item>
        </el-carousel>-->
      </div>
    </section>
    <!-- <section class="recommend">
      <div class="blockTitle produsBg">推荐</div>
      <div class="recommendItem">
        <el-row>
          <el-col :span="16" class="center">
            <img src="/static/image/recommend.png" />
          </el-col>
          <el-col :span="8" class="recommendCon">
            <div>168Node为您推荐了ETH 2.0的服务</div>
            <p>优质的节点代建服务</p>
            <button
              type="button"
              router-link
              @click="$router.push('/construction')"
              class="normalBtn"
            >节点代建</button>
          </el-col>
        </el-row>
      </div>
    </section>-->
    <!-- <hr class="dividingLine" />
    <section class="product">
      <div class="blockTitle produsBg">云算力</div>
      <div class="noData" v-if="contractData.length == 0">
        <img src="/static/image/noData.png" />
        <p>暂无数据</p>
      </div>
      <div class="productCon" v-else>
        <div class="homeMore">
          <router-link to="/cloudPower" class="more">查看更多</router-link>
        </div>
        <contract-components
          v-for="(item,index) in contractData"
          :key="item+index"
          :contractData="item"
          :isRealBuy="false"
        />
      </div>
      <hr class="dividingLine" />
    </section>-->
    <!-- <section class="nodeInfo">
      <div class="blockTitle produsBg">Staking</div>
      <div class="nodeData">
        <div class="homeMore">
          <router-link to="/staking" class="more">查看更多</router-link>
        </div>
        <div class="nodeDataCon">
          <div v-for="(item,index) in nodeData" :key="index" class="nodeItem">
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
              <a :href="item.website" class="roundBtn rimBtn" target="_blank">了解更多</a>
              <router-link
                :to="'/nodeVote/'+item.id"
                class="roundBtn rimBtn"
                v-show="item.isOnline"
              >投票</router-link>
            </div>
          </div>
        </div>
      </div>
    </section>-->
    <!-- <section class="chooseUs">
      <div class="blockTitle aboutUsBg">选择我们</div>
      <div class="chooseUsCon">
        <div v-for="(item,index) in chooseUs" :key="index" class="chooseUsItem">
          <div class="chooseUsItemImg">
            <img :src="item.image" />
          </div>
          <div class="chooseUsTitle">{{item.title}}</div>
          <div>{{item.content}}</div>
        </div>
      </div>
    </section>-->
    <!-- <section class="mine">
      <div class="blockTitle aboutUsBg">机房实景</div>
      <div class="mineCon">
        <el-carousel :interval="4000" type="card" height="400px" indicator-position="none">
          <el-carousel-item v-for="(item,index) in engineRoom" :key="index">
            <img :src="item.image" height="80%" width="100%" />
          </el-carousel-item>
        </el-carousel>
      </div>
    </section>-->
  </div>
</template>

<script>
import nodeInfo from "@/assets/localData/nodeInfo";
import contractComponents from "@/components/comm/contractComponents";
import currencyData from "@/assets/localData/currency";

export default {
  name: "home",
  components: { contractComponents },
  data() {
    return {
      noticeData: [],
      chooseUs: [
        {
          image: "/static/image/chooseUs1.png",
          title: "安全",
          content: "顶尖安全团队，全方位一体化安全机制保障"
        },
        {
          image: "/static/image/chooseUs2.png",
          title: "高效",
          content: "专业区块链团队深入研究各种共识机制，最大化挖矿效率"
        },
        {
          image: "/static/image/chooseUs3.png",
          title: "稳定",
          content: "资深运维团队维护机房平稳运行，达到金融核心系统级别要求"
        },
        {
          image: "/static/image/chooseUs4.png",
          title: "影响力",
          content: "强化社会建设，融入公链生态环境，提供基础设施，参与见证节点"
        }
      ],
      contractData: [],
      nodeData: nodeInfo.nodeData.slice(0, 5),
      bannerData: [],
      idcData: [
        {
          id: "01",
          title: "安全",
          image: "/static/image/idcImage01.png"
        },
        {
          id: "02",
          title: "稳定",
          image: "/static/image/idcImage02.png"
        },
        {
          id: "03",
          title: "高效",
          image: "/static/image/idcImage03.png"
        }
      ],
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
          text: "运维团队拥有大规模服务器运维经验"
        }
      ],
      partnerData: [
        {
          image: "/static/image/crustLogo.png"
        },
        {
          image: "/static/image/wujilian.png"
        },
        {
          image: "/static/image/polkadot.png"
        },
        {
          image: "/static/image/ksmLogo.png"
        },
        {
          image: "/static/image/wuji.png"
        },
        {
          image: "/static/image/powerZ.png"
        },
        {
          image: "/static/image/phalaLogo.png"
        }
      ],
      // engineRoom: [
      //   {
      //     image: "/static/image/engineRoom1.png"
      //   },
      //   {
      //     image: "/static/image/engineRoom2.png"
      //   },
      //   {
      //     image: "/static/image/engineRoom3.png"
      //   },
      //   {
      //     image: "/static/image/engineRoom4.png"
      //   },
      //   {
      //     image: "/static/image/engineRoom5.png"
      //   },
      //   {
      //     image: "/static/image/engineRoom6.png"
      //   }
      // ]
      swiperOption: {
        slidesPerView: 4,
        spaceBetween: 30,
        loop: true,
        loopFillGroupWithBlank: true,
        pagination: {
          el: ".swiper-pagination",
          clickable: true
        },
        navigation: {
          nextEl: ".swiper-button-next",
          prevEl: ".swiper-button-prev"
        }
      }
    };
  },
  methods: {
    // banner
    getBanner() {
      if (!localStorage.getItem("banner")) {
        this.$api.getBanner().then(res => {
          this.bannerData = res.data;
          console.log(res);
          localStorage.setItem("banner", JSON.stringify(res.data));
        });
      } else {
        this.bannerData = JSON.parse(localStorage.getItem("banner"));
      }
    },
    // 公告
    getNotice() {
      this.$api.getNotice({ page: 1, size: 2 }).then(res => {
        this.noticeData = res.data;
      });
    },
    // 跳转
    linkTo(linkUrl) {
      if (linkUrl) {
        window.open(linkUrl, "_blank");
      }
    },
    // 合约包
    getContractList() {
      this.$api.getContractList({ isRecommend: 1 }).then(res => {
        let result = res.data;
        result.map(item => {
          let index = currencyData.currency.findIndex(
            a => a.value == item.projectType
          );
          item.powerUnit = currencyData.currency[index].powerUnit;
          item.number = 1;
          item.maxByNumber =
            item.restComputingPower == null
              ? 1
              : Math.floor(item.restComputingPower / item.unitComputingPower);
        });
        this.contractData = result;
      });
    },
    //滑动
    move(e) {
      let odiv = e.currentTarget; //获取目标元素
      //算出鼠标相对元素的位置
      let disX = e.clientX - odiv.offsetLeft;
      document.onmousemove = e => {
        //鼠标按下并移动的事件
        //用鼠标的位置减去鼠标相对元素的位置，得到元素的位置
        let left = e.clientX - disX;

        //移动当前元素
        odiv.style.left = left + "px";
      };
      document.onmouseup = e => {
        odiv.className = "partnerCon amit";
        odiv.style.left = 0 + "px";
        document.onmousemove = null;
        document.onmouseup = null;
        setTimeout(() => {
          odiv.className = "partnerCon";
        }, 300);
      };
    },
    prev() {
      this.$refs.mySwiper.$swiper.slidePrev();
    },
    next() {
      this.$refs.mySwiper.$swiper.slideNext();
    }
  },
  mounted() {
    this.getNotice();
    this.getBanner();
    // this.getContractList();
  }
};
</script>
<style  scoped>
.homeInfo {
  padding-bottom: 22px;
}
.bulletin {
  font-size: 14px;
  padding: 10px 0;
  box-sizing: border-box;
  background: rgba(245, 249, 255, 1);
}
.bulletin > div {
  width: 1000px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.bulletinCon {
  flex: 1;
  padding: 0 40px;
  display: flex;
  justify-content: space-between;
}
.bulletinItem {
  width: 40%;
  cursor: pointer;
}
.bulletinItem span {
  display: inline-block;
  width: 40%;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
.bulletinItem span:last-child {
  color: rgba(102, 102, 102, 1);
}
.mining {
  padding-top: 27px;
}
.miningItem {
  padding-bottom: 122px;
  background: linear-gradient(to right, #1a202b, #292e38);
}
.miningItem .el-row {
  height: 100%;
  width: 1200px;
  margin: 0 auto;
}
.miningCon {
  padding-top: 151px;
  padding-left: 135px;
}
.miningCon div {
  margin-bottom: 35px;
}
.miningCon div strong {
  font-size: 30px;
}
.miningCon div:nth-of-type(1) {
  font-size: 22px;
  width: 254px;
}
.miningCon div:nth-of-type(2) {
  font-size: 22px;
  width: 189px;
}
.mining_sty {
  display: inline-block;
  background: linear-gradient(to right, #1587ed, #3dd399);
  border-radius: 10px;
}
.miningBtn {
  padding: 18px 35px;
  color: rgba(255, 255, 255, 1);
  background-color: transparent;
  border-radius: 10px;
  border-color: transparent;
  font-size: 18px;
  text-align: center;
  cursor: pointer;
}

.idc {
  padding-top: 80px;
}

.idcCon {
  width: 1400px;
  height: 360px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  /* border-bottom: 11px solid #1a202b; */
  border-bottom-width: 11px;
  border-bottom-style: solid;
  border-bottom-color: #1a202b;
  border-top-width: 0px;
  border-left-width: 0px;
  border-right-width: 0px;
  border-image: linear-gradient(to right, #1587ed, #3dd399) 20 20;
  /* border: 1px solid #ffffff; */
}
.idcItem {
  width: 33.3%;
  height: 325px;
  box-sizing: border-box;
  padding-top: 40px;
  border: 2px solid #178be8;
  border-color: transparent;
  border-radius: 5px 5px 0 0;
  transition: all 0.3s;
  background: linear-gradient(to right, #282d38, #1a202b) no-repeat;
}
.idcItem:hover {
  border-color: #178be8;
  height: 355px;
}
.idcItem img {
  display: block;
  margin: 0 auto;
}
.idcItem div {
  padding-left: 40px;
  font-size: 22px;
  margin-bottom: 10px;
}
.idcItem div strong {
  font-size: 36px;
}
.homeAbout {
  padding-top: 120px;
}
.partner {
  padding-bottom: 100px;
}
.partnerMask {
  width: 100%;
  height: 200px;
  background: linear-gradient(to right, #292e38, #1a202b);
  position: relative;
}
.partnerMask /deep/ .el-carousel__mask {
  background-color: transparent;
}
.boxs {
  width: 100%;
  height: 100%;
  margin: 0 auto;
  /* overflow: hidden; */
  position: relative;
}
.partnerCon {
  width: 1400px;
  height: 100%;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  position: absolute;
  cursor: pointer;
  box-sizing: border-box;
  padding: 0 5%;
}
.amit {
  transition: all 0.3s;
}
.partnerLb {
  width: 1200px;
  margin: 0 auto;
}
.partnerLb-item {
  display: flex;
  justify-content: center;
  align-items: center;
}

.partnerItem {
  /* flex: 1; */
  flex-grow: 1;
  display: flex;
  justify-content: center;
  background: transparent;
  align-items: center;
  transition: all 0.3s;
  box-sizing: border-box;
  padding: 0 40px;
}
.partnerItem:hover {
  background: #292e38;
  border-radius: 10px;
}
.partnerItem img {
  display: block;
  width: 100%;
  /* width: 170px; */
}
.swiper1 {
  width: 1400px;
  height: 100%;
  cursor: pointer;
}
.swiper1Item {
  display: flex;
  justify-content: center;
  align-items: center;
}
.swiperMask {
  width: 1400px;
  height: 100%;
  margin: 0 auto;
  display: flex;
  justify-content: center;
  align-items: center;
}
.swiperMask .swiper-button-prev,
.swiper-button-next {
  position: static;
  color: #fff;
}

/* .recommend {
  margin: 70px 0;
}
.recommendItem {
  padding-top: 20px;
  background: url("/static/image/bg6.png") no-repeat, rgba(249, 251, 255, 1);
  background-position: right bottom;
}
.recommendItem .el-row {
  width: 1200px;
  margin: 0 auto;
}
.recommendCon {
  color: rgba(112, 112, 112, 1);
  margin-top: 50px;
}
.recommendCon > div {
  width: 300px;
  font-weight: 550;
  font-size: 32px;
  color: rgba(31, 31, 31, 1);
}
.recommendCon p {
  color: rgba(73, 150, 255, 1);
  margin: 50px 0;
} */
.more1 {
  color: rgba(112, 116, 255, 1);
  border: none;
  outline: none;
  background: transparent;
  cursor: pointer;
}
.more {
  color: rgba(102, 102, 102, 1);
  border-bottom: 1px solid rgba(102, 102, 102, 1);
  outline: none;
  background: transparent;
  cursor: pointer;
}
.homeMore {
  text-align: right;
  margin: 30px 0;
}
.product {
  padding: 40px 0;
  background: url("/static/image/bg2.png") no-repeat;
  background-position: left bottom;
}
.productCon {
  width: 1200px;
  margin: 32px auto 100px auto;
}
.chooseUs {
  background-size: 100% 100%;
  padding: 80px 0 0 0;
}
.chooseUsCon {
  width: 1200px;
  margin: 53px auto 0 auto;
  display: flex;
  justify-content: space-between;
}
.chooseUsItem {
  width: 260px;
  height: 330px;
  padding: 50px 20px;
  box-sizing: border-box;
  text-align: center;
  color: rgba(164, 179, 192, 1);
}
.chooseUsItemImg {
  width: 90px;
  height: 90px;
  margin: 0 auto;
  display: flex;
  justify-content: space-around;
  align-items: center;
}
.chooseUsTitle {
  font-weight: 600;
  line-height: 70px;
  color: rgba(67, 67, 67, 1);
  font-size: 18px;
}
.partner {
  padding-top: 35px;
}
/* .nodeInfo {
  padding: 30px 0;
  background: linear-gradient(
    to bottom,
    transparent 0%,
    transparent 60%,
    rgba(245, 249, 255, 1) 61%,
    rgba(245, 249, 255, 1) 100%
  );
} */
.nodeData {
  width: 1200px;
  margin: 0 auto;
}

.mine {
  /* background: url("/static/image/bg1.png") no-repeat; */
  background-size: contain;
  background-position: left bottom;
  padding: 30px 0 150px 0;
}
.mineCon {
  width: 1200px;
  margin: 35px auto;
}
</style>
