<template>
  <div id="app" ref="app">
    <el-scrollbar style="height:100%" ref="scroll">
      <router-view />
    </el-scrollbar>
  </div>
</template>

<script>
export default {
  name: "App",
  mounted() {
    // 关闭浏览器窗口的时候清空浏览器缓存在localStorage的数据
    window.onbeforeunload = function(e) {
      var storage = window.localStorage;
      storage.removeItem("banner");
    };
  },
  watch: {
    //监听路由跳转将页面调回最顶部
    $route() {
      this.$refs.scroll.wrap.scrollTop = 0;
    }
  }
};
</script>

