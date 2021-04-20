<template>
  <div class="aboutUs">
    <img src="/static/image/aboutUsBg.png" />
    <router-view />
  </div>
</template>
<script>
export default {
  name: "aboutUs",
  data() {
    return {};
  }
};
</script>
<style  scoped>
.aboutUs > img {
  position: relative;
  z-index: -1;
  display: block;
  width: 2134px;
}
</style>

