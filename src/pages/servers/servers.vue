<template>
  <div class="serversInfo">
    <div class="nodeitem" v-for="item in serversData" :key="item.id">
      <div class="voteSelect">
        <p>{{ item.productModel }}</p>
      </div>
      <div class="nodeitemCon">
        <div class="nodeitemMsg">
          <div>
            CPU:
            <b>{{ item.cpu }}</b>
          </div>
          <div>
            存储空间:
            <b>{{ item.rom }}</b>
          </div>
          <div>
            适用算法:
            <b>{{ item.algorithm }}</b>
          </div>
          <div class="mining_sty">
            <router-link :to="'/serversNode/' + item.id" class="miningBtn"
              >查看详情</router-link
            >
          </div>
        </div>
        <div class="nodeitemMsg">
          <img class="nodeitemImg" :src="item.image" alt />
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import serversMessage from "@/assets/localData/serversMessage";
export default {
  name: "home",
  data() {
    return {
      serversData: serversMessage.serversData,
    };
  },
};
</script>
<style scoped>
.serversInfo {
  padding-bottom: 200px;
}
.miningBtn {
  line-height: 60px;
}
</style>