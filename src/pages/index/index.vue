<template>
  <view>
    <Swiper :images="images" />
    <ul>
      <li v-for="(item, index) in list" :key="index">
        <a :href="item.url">
          <img :src="item.images" mode="scaleToFill" />
          <span>{{item.title}}</span>
        </a>
      </li>
    </ul>
    <button @click="ajax()">4444</button>
    <!-- <button open-type="getUserInfo" @getuserinfo="bindGetUserInfo" @click="getUserInfoClick">获取权限</button> -->
    <button
      v-if="buttonVisible"
      open-type="getUserInfo"
      @getuserinfo="bindGetUserInfo"
      @click="getUserInfoClick"
    >获取权限</button>
  </view>
</template>
<script>
import Swiper from "@/components/swiper";
export default {
  components: { Swiper },
  data() {
    return {
      code: "", //wx.login拿回来的code
      buttonVisible: false,
      images: [
        {
          url:
            "https://img-oss.yunshanmeicai.com/goods/default/31d8dfa4-0d7b-4694-80f9-41b07c9d0a3a.png"
        },
        {
          url:
            "https://img-oss.yunshanmeicai.com/goods/default/e83c8f0f-4acc-4729-bcbb-294f2b314977.jpg"
        }
      ],
      list: [
        {
          title: "活动",
          url: "../activity/main",
          images:
            "https://img-oss.yunshanmeicai.com/goods/default/31d8dfa4-0d7b-4694-80f9-41b07c9d0a3a.png"
        },
        {
          title: "问卷",
          url: "../questionnaire/index/main",
          images:
            "https://img-oss.yunshanmeicai.com/goods/default/e83c8f0f-4acc-4729-bcbb-294f2b314977.jpg"
        },
        {
          title: "夏令营",
          images:
            "https://img-oss.yunshanmeicai.com/goods/default/e83c8f0f-4acc-4729-bcbb-294f2b314977.jpg"
        },
        {
          title: "课程",
          images:
            "https://img-oss.yunshanmeicai.com/goods/default/31d8dfa4-0d7b-4694-80f9-41b07c9d0a3a.png"
        }
      ]
    };
  },
 
  mounted() {
    const self = this;
    wx.login({
      success(res) {
        if (res.code) {
          // 这里可以把code传给后台，后台用此获取openid及session_key
          self.code = res.code;
          self.wxGetUserInfo(res.code);
        }
      }
    });
  },
  methods: {
    wxGetUserInfo(code) {
      const self = this;
      wx.getUserInfo({
        withCredentials: true,
        success(res) {
          //自动获取用户信息res
          self.$fly
            .post("https://mp.zymcloud.com/hp-hd/applet/activity/getAppid", {
              code
            })
            .then(res => {
              console.log(`后台交互拿回数据:`, res);
              // 获取到后台重写的session数据，可以通过vuex做本地保存
              wx.setStorage({
                key: "openid",
                data: res.data.data.openid
              });
              wx.setStorage({
                key: "session_key",
                data: res.data.data.session_key
              });
            })
            .catch(err => {
              console.log(`自动请求api失败 err:`, err);
            });
        },
        fail(err) {
          console.log("自动wx.getUserInfo失败:", err);
          // 显示主动授权的button
          self.buttonVisible = true;
        }
      });
    },
    bindGetUserInfo(e) {
      // console.log('回调事件后触发')
      const self = this;
      if (e.mp.detail.userInfo) {
        console.log("用户按了允许授权按钮");

        self.$fly
          .post("https://mp.zymcloud.com/hp-hd/applet/activity/getAppid", {
            // 这里的code就是通过wx.login()获取的
            code: self.code
            
          })
          .then(res => {
            console.log(`后台交互拿回数据:`, res);
            // 获取到后台重写的session数据，可以通过vuex做本地保存
            wx.setStorage({
                key: "openid",
                data: res.data.data.openid
              });
              wx.setStorage({
                key: "session_key",
                data: res.data.data.session_key
              });
          })
          .catch(err => {
            console.log(`api请求出错:`, err);
          });
      } else {
        //用户按了拒绝按钮
        console.log("用户按了拒绝按钮");
      }
    }
  },
  computed: {}
};
</script>
<style>
.wrapper {
  width: 90%;
  height: 40%;
  background-color: #fff;
  border-radius: 4px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.wechat {
  margin-top: 80rpx;
  display: block;
  width: 70rpx;
  height: 70rpx;
  border-radius: 50%;
}
.hint {
  margin-top: 30rpx;
}
button {
  width: 70%;
  height: 100rpx;
  background-color: #259b24;
  border-radius: 70rpx;
  margin-top: 60rpx;
}
.sec-mask {
  background: rgba(0, 0, 0, 0.4);
  position: fixed;
  display: flex;
  justify-content: center;
  align-items: center;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
}
.title {
  margin: 20rpx 0 35rpx;
}
.input {
  height: 41rpx;
  border-bottom: 1px solid #000;
}
.btn {
  width: 70%;
  height: 100rpx;
  background-color: #259b24;
  color: #fff;
  margin: 80rpx auto;
  border-radius: 4px;
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: center;
}
body {
  background-color: #eee;
}
ul {
  width: 100%;
  margin-top: 40px;
}
li {
  padding: 10px;
  float: left;
  width: 50%;
  height: 230px;
  text-align: center;
  list-style: none;
  box-sizing: border-box;
}
li a {
  background: white;
}
li a image {
  width: 100%;
  height: 167.5px;
}
li a span {
  display: inline-block;
  padding: 10px 0;
}
</style>
