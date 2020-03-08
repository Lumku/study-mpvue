<template>
  <div>
    <a href="/pages/counter/main" class="counter">去往Vuex示例页面</a>
    <ul>
      <li
        @click="handleClick(item.cinemaId)"
        v-for="item in dataList"
        :key="item.cinemaId"
      >{{item.name}}</li>
    </ul>
  </div>
</template>

<script>
import card from "@/components/card";

export default {
  data() {
    return {
      dataList: [],
      motto: "Hello miniprograme",
      userInfo: {
        nickName: "mpvue",
        avatarUrl: "http://mpvue.com/assets/logo.png"
      }
    };
  },

  components: {
    card
  },

  methods: {
    bindViewTap() {
      const url = "../logs/main";
      if (mpvuePlatform === "wx") {
        mpvue.switchTab({ url });
      } else {
        mpvue.navigateTo({ url });
      }
    },
    clickHandle(ev) {
      console.log("clickHandle:", ev);
      // throw {message: 'custom test'}
    },
    handleClick(id) {
      console.log(id);
      mpvue.navigateTo({
        url: "/pages/detail/main?id=" + id
      });
    }
  },

  created() {
    // let app = getApp()
  },
  mounted() {
    if (mpvuePlatform === "wx") {
    }
  },
  onPullDownRefresh() {
    console.log("下拉刷新");
    setTimeout(() => {
      mpvue.request({
        url:
          "https://m.maizuo.com/gateway?cityId=110100&ticketFlag=1&k=1681818",
        header: {
          "X-Client-Info":
            '{"a":"3000","ch":"1002","v":"5.0.4","e":"1583647283532575945257","bc":"110100"}',
          "X-Host": "mall.film-ticket.cinema.list"
        },
        success: ({ data: res }) => {
          console.log(res);
          this.dataList = res.data.cinemas;
          console.log(this.dataList);
        }
      });
      mpvue.stopPullDownRefresh();
    }, 2000);
  },
  onReachBottom() {
    console.log("到底了");
  }
};
</script>

<style scoped>
li {
  margin: 10px;
}

.userinfo {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.userinfo-avatar {
  width: 128rpx;
  height: 128rpx;
  margin: 20rpx;
  border-radius: 50%;
}

.userinfo-nickname {
  color: #aaa;
}

.usermotto {
  margin-top: 150px;
}

.form-control {
  display: block;
  padding: 0 12px;
  margin-bottom: 5px;
  border: 1px solid #ccc;
}
.all {
  width: 7.5rem;
  height: 1rem;
  background-color: blue;
}
.all:after {
  display: block;
  content: "";
  clear: both;
}
.left {
  float: left;
  width: 3rem;
  height: 1rem;
  background-color: red;
}

.right {
  float: left;
  width: 4.5rem;
  height: 1rem;
  background-color: green;
}
</style>
