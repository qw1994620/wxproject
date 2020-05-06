<template>
  <div>
    <div class="iconfont btn" :class="{iconmusic:flag,iconziyuan:!flag}" @click="play()"></div>
    <div></div>
  </div>
</template>

<script>
export default {
  props: {},
  data() {
    return {
      flag: true,
      music: ""
    };
  },
  computed: {},
  updated() {},
  onLound() {},
  mounted() {
    this.player(wx.getBackgroundAudioManager());
  },
  watch: {},
  methods: {
    player(audio) {
      this.$fly
        .post("https://mp.zymcloud.com/hp-hd/applet/activity/list", {
          activityId: 1
          // openid:res.data
        })
        .then(res => {
          this.music = res.data.data.hdActivity.music; //背景音乐数据渲染 向组件传值
          
          var that = this;
          //title不写或放空会报错哦，即使不报错ios系统会不播放，所以必须加
          audio.title = "瞬间的永恒";

          //这点需知微信小程序上线不能超过2M,音乐文件会很大，所以要放在服务器上才可以
          audio.src = this.music;

          //音乐播放结束后继续播放此音乐，循环不停的播放
          audio.onEnded(() => {
            that.player(wx.getBackgroundAudioManager());
          });
        })
        .catch(err => {
          console.log(`自动请求api失败 err:`, err);
        });
    },
    play() {
      if (this.flag) {
        wx.getBackgroundAudioManager().pause();
        this.flag = !this.flag;
      } else {
        wx.getBackgroundAudioManager().play();
        this.flag = !this.flag;
      }
    }
  },
  components: {}
};
</script>

<style scoped >
.icon {
  width: 1em;
  height: 1em;
  vertical-align: -0.15em;
  fill: currentColor;
  overflow: hidden;
}
.color {
  background-color: blue;
}
.btn {
  display: inline-block;
  font-size: 40px;
  color: green;
  transform-origin: center center;
  animation: rotate 3s linear infinite;
}
@keyframes rotate {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
</style>
