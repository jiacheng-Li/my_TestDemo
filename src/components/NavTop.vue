<template>
  <div class="NavTop" :class="transparentPage.includes(active)?'transparentBg':'coloredBg'">
    <div class="NavCon">
      <div class="logo">
        <router-link to="/home">
          <img src="/static/image/logo.png" />
        </router-link>
      </div>
      <ul>
        <li v-for="(item,index) in menuList" :key="index">
          <div>
            <router-link
              :to="item.link"
              :class="{'navActive':active.indexOf(item.active) != -1}"
            >{{item.title}}</router-link>
            <div v-if="item.link==='/aboutUs'" class="aboutUs-select">
              <ul class="aboutUsList">
                <li v-for="(items,indexnum) in aboutUsNavData" :key="indexnum">
                  <router-link
                    :to="items.path"
                    :class="{'aboutUsActive':aboutUsActive.indexOf(items.active) != -1}"
                  >{{items.title}}</router-link>
                </li>
              </ul>
            </div>
          </div>
        </li>
      </ul>
      <!-- <div class="logInRegister">
        <div v-if="$store.state.info == ''">
          <router-link to="/login">登录</router-link>/
          <router-link to="/register">注册</router-link>
        </div>
        <div v-if="$store.state.info !== ''" class="user">
          <router-link to="/userCloudPower">
            <img src="/static/image/avatar.png" />
            <span>{{$store.state.info.nickName}}</span>
          </router-link>
          <ul class="Navchildren">
            <li>
              <a @click="signOut" class="signOut">退出登录</a>
            </li>
          </ul>
        </div>
      </div>-->
      <!-- <div class="logInRegister">
        <div class="user">
          <span>app下载</span>
          <div class="Navchildren">
            <img src="/static/image/appDownload.png" width="150" />
          </div>
        </div>
      </div>-->
    </div>
  </div>
</template>
<script>
export default {
  name: "navTop",
  data() {
    return {
      active: "",
      transparentPage: ["home"],
      menuList: [
        {
          title: "首页",
          active: "home",
          link: "/"
        },
        // {
        //   title: "云算力",
        //   active: "cloudPower",
        //   link: "/cloudPower"
        // },
        {
          title: "服务器",
          active: "servers",
          link: "/servers"
        },
        {
          title: "数据中心",
          active: "recordsCenter",
          link: "recordsCenter"
        },
        {
          title: "Staking",
          active: "staking",
          link: "/staking"
        },
        {
          title: "矿池app",
          active: "construction",
          link: "/construction"
        },
        {
          title: "关于我们",
          active: "aboutUs",
          link: "/aboutUs"
        }
      ],
      aboutUsActive: "",
      aboutUsNavData: [
        {
          title: "关于我们",
          path: "/aboutUs",
          active: "aboutUsCon"
        },
        {
          title: "公告",
          path: "/bulletin",
          active: "bulletin"
        }
      ]
    };
  },
  methods: {
    // 退出登录
    signOut() {
      this.$api.signOut().then(res => {
        localStorage.setItem("passport", "");
        this.$router.push({ path: "/" });
        this.$store.dispatch("getInfo", "");
      });
    }
  },
  mounted() {
    this.active = this.$route.meta.active;
    this.aboutUsActive = this.$route.meta.active;
  },
  watch: {
    // 路由监听
    $route: function(to, from) {
      this.active = this.$route.meta.active;
      this.aboutUsActive = this.$route.meta.active;
      // console.log(this.$route.meta.active);
      // console.log(this.aboutUsActive.indexOf(this.aboutUsNavData[1].active));
    }
  }
};
</script>
<style  scoped>
.logo {
  line-height: 70px;
}
.coloredBg {
  background: rgba(244, 249, 252, 1);
}
.transparentBg {
  background: transparent;
  position: absolute;
  left: 0;
  top: 0;
  z-index: 3;
}
.NavTop {
  height: 70px;
  width: 100%;
  background: #20252e;
}
.NavCon {
  width: 1200px;
  height: 100%;
  margin: 0 auto;
  display: flex;
  justify-content: flex-end;
}
.NavCon > ul {
  height: 100%;
  width: 100%;
  display: flex;
  justify-content: flex-end;
}
.NavCon > ul > li {
  margin-right: 40px;
}
.NavCon > ul > li > div > a {
  display: inline-block;
  padding: 0 20px;
  height: 70px;
  line-height: 70px;
  color: #ffffff;
}
.NavCon > ul > li {
  position: relative;
}
.NavCon > ul > li > div > a:hover {
  cursor: pointer;
  /* background: rgba(255, 255, 255, 1);
  box-shadow: 0px 3px 6px rgba(73, 150, 255, 0.21);
  color: rgba(73, 150, 255, 1) !important; */
  border-bottom-width: 5px;
  border-bottom-style: solid;
  border-bottom-color: #fff;
  border-top-width: 0px;
  border-left-width: 0px;
  border-right-width: 0px;
  border-image: linear-gradient(to right, #1587ed, #3dd399) 20 20;
  box-sizing: border-box;
  /* border: 3px solid #ffffff;
  border-image: linear-gradient(to right, #1587ed, #3dd399) 20 20; */
}
.navActive {
  border-bottom-width: 5px;
  border-bottom-style: solid;
  border-bottom-color: #fff;
  border-top-width: 0px;
  border-left-width: 0px;
  border-right-width: 0px;
  border-image: linear-gradient(to right, #1587ed, #3dd399) 20 20;
  /* -webkit-border-image: linear-gradient(to right, #1587ed, #3dd399) 20 20; */
  box-sizing: border-box;
  /* background: rgba(255, 255, 255, 1); */
  /* box-shadow: 0px 3px 6px rgba(73, 150, 255, 0.21); */
  /* color: rgba(73, 150, 255, 1) !important; */
  font-size: 16px;
}
.logInRegister {
  width: 100px;
  text-align: right;
  line-height: 70px;
  color: #ffffff;
}
.logInRegister a,
.user span {
  color: #ffffff;
}
.user {
  cursor: pointer;
  width: 100%;
  position: relative;
  text-align: right;
}
.user > a {
  display: inline-block;
  box-sizing: border-box;
  width: 100px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  text-align: right;
  color: rgba(0, 100, 251, 1) !important;
  padding: 0 10px;
}
.Navchildren {
  background: rgba(255, 255, 255, 1);
  box-shadow: 0px 3px 6px rgba(73, 150, 255, 0.21);
  min-width: 100px;
  text-align: center;
  position: absolute;
  left: 50%;
  top: 70px;
  transform: translateX(-50%);
  z-index: 4;
  display: none;
}
.Navchildren li {
  line-height: 38px;
  padding: 0 10px;
}
.Navchildren li a .user {
  display: inline-block;
  width: 100%;
  height: 100%;
  white-space: nowrap;
  color: rgba(0, 0, 0, 1);
}
.user:hover > a {
  background: rgba(255, 255, 255, 1);
  box-shadow: 0px 3px 6px rgba(73, 150, 255, 0.21);
}
.user:hover .Navchildren {
  display: block;
}

.signOut {
  color: rgba(102, 102, 102, 1);
}
.aboutUs-select {
  display: none;
}
.NavCon > ul > li:nth-of-type(6) > div:hover .aboutUs-select {
  display: block;
}
.aboutUsList {
  background: #292e38;
}
.aboutUsList > li {
  height: 40px;
}
.aboutUsList > li > a {
  display: block;
  width: 100%;
  font-size: 14px;
  line-height: 40px;
  padding-left: 6px;
  color: #fff;
}
.aboutUsList > li > a:hover {
  color: #3ac998;
}
.aboutUsActive {
  color: #3ac998;
}
</style>
