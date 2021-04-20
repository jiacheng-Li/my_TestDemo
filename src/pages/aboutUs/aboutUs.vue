<template>
  <div class="aboutUs">
    <section class="companyProfile">
      <div class="companyCon">
        <p class="center">168Node成立于2019年，由矿业巨头无极链科技投资孵化，致力于打造区块链基础设施建设与运营综合服务平台。</p>
        <p class="center">团队核心成员由区块链资深从业专家、分布式存储专家、资深IT工程师和硬件工程师等组成。</p>
        <p>168Node依托自有&联盟的矿场与数据中心，拥有自主软硬件技术及专业化运维团队，涉及业务包括服务器研发、服务器销售，服务器托管、节点搭建及配套软件服务等业务。</p>
        <p>团队深耕IPFS/Crust领域，打造了以分布式存储为核心的生态体系，努力为用户提供安全、稳定、高效、可靠的区块链服务，不断为用户创造更多价值。</p>
      </div>
    </section>

    <!-- <section class="realScene">
      <div class="sceneImg">
        <el-carousel :interval="4000" type="card" height="320px" indicator-position="none">
          <el-carousel-item v-for="(item,index) in engineRoom" :key="index">
            <div class="sceneImgItem">
              <img :src="item.image" height="80%" width="100%" />
              <div>{{item.description}}</div>
            </div>
          </el-carousel-item>
        </el-carousel>
      </div>
    </section>-->
    <section class="contactUs">
      <div class="weChatHover">
        <!-- <button type="button" class="weChatHoverButton">联系我们</button> -->
        <div class="idcBtn weChatHoverButton">
          <div class="idcBtn_sty">
            <button type="button" class="moreBtn">联系我们</button>
          </div>
        </div>
        <div class="weChat">
          <div>
            <img src="/static/image/poolUser.png" />
            <p>官方微信二维码客服</p>
          </div>
          <div>
            <img src="/static/image/officailAccount.jpg" />
            <p>官方微信公众号</p>
          </div>
          <!-- <div>
            <img src="/static/image/businessCooperation.png" />
            <p>商务合作邮箱：783752764@qq.com</p>
          </div>-->
        </div>
      </div>
    </section>
  </div>
</template>
<script>
export default {
  name: "aboutUs",
  data() {
    return {
      // engineRoom: [
      //   {
      //     image: "/static/image/engineRoom1.png",
      //     description: "散热风扇"
      //   },
      //   {
      //     image: "/static/image/engineRoom2.png",
      //     description: "配电室"
      //   },
      //   {
      //     image: "/static/image/engineRoom3.png",
      //     description: "机房走廊"
      //   },
      //   {
      //     image: "/static/image/engineRoom4.png",
      //     description: "机房走廊"
      //   },
      //   {
      //     image: "/static/image/engineRoom5.png",
      //     description: "机房走廊"
      //   },
      //   {
      //     image: "/static/image/engineRoom6.png",
      //     description: "控制室"
      //   }
      // ]
    };
  }
};
</script>
<style scoped>
.companyProfile {
  margin-top: -170px;
  padding: 40px 0 80px 0;
}
.companyCon {
  width: 1300px;
  margin: 0 auto;
  background: #20252e;
  color: #ffffff;
  padding: 80px 20px;
  font-size: 16px;
  border-radius: 5px;
}
.companyCon p {
  width: 100%;
  margin: 10px auto;
  text-align: center;
}

.companyImg {
  display: flex;
  justify-content: space-between;
  margin: 33px 0;
}
.companyImg > div {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.contactUs {
  /* padding: 60px 0 80px 0; */
  padding-bottom: 300px;
}
.weChatHover {
  position: relative;
  width: 164px;
  margin: 0 auto;
}

.moreBtn {
  padding: 18px 30px;
  font-size: 22px;
}
.weChat {
  width: 413px;
  background: #20252e;
  display: flex;
  justify-content: space-around;
  text-align: center;
  font-size: 12px;
  /* border: 1px solid #0064fb; */
  border-radius: 5px;
  padding: 40px 20px;
  position: absolute;
  left: 50%;
  bottom: -218px;
  transform: translateX(-50%);
  opacity: 0;
  transition: all 0.3s;
}
.weChat p {
  color: rgba(245, 245, 245, 0.8);
}
.weChat img {
  width: 92px;
  height: 92px;
  vertical-align: middle;
}
.weChat > div:nth-of-type(3) {
  padding-top: 20px;
}
.weChat > div:nth-of-type(3) img {
  width: 84px;
  height: 67px;
  margin-bottom: 5px;
}

.weChatHover .weChatHoverButton:hover + .weChat {
  opacity: 1;
}
.weChatHover .weChatHoverButton:hover .moreBtn {
  background: transparent;
}
.realScene {
  padding: 70px 0;
}
.sceneImg {
  width: 1200px;
  margin: 20px auto;
}
.sceneImgItem {
  height: 100%;
  display: flex;
  justify-content: space-between;
  flex-direction: column;
}
.sceneImg {
  margin: 40px auto;
}
.sceneImgItem img {
  width: 100%;
  height: 270px;
}
.sceneImgItem div {
  text-align: center;
  padding: 10px 0;
}
.pageTitle {
  font-size: 24px;
  text-align: center;
}
</style>

