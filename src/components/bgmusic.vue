<template>
  <div>
    <div class="iconfont btn" :class="{iconmusic:flag,iconziyuan:!flag}" @click="play()"></div>
    <div>
 
</div>
  </div>
</template>

<script>
export default {
  props: [],
  data() {
    return {
      flag: true
    };
  },
  computed: {},
  created() {},
  mounted() {
    this.player(wx.getBackgroundAudioManager());
  },
  watch: {},
  methods: {
    player(audio) {
      console.log(audio);

      var that = this;
      //title不写或放空会报错哦，即使不报错ios系统会不播放，所以必须加
      audio.title = "瞬间的永恒";

      //这点需知微信小程序上线不能超过2M,音乐文件会很大，所以要放在服务器上才可以
      audio.src =
        "https://sharefs.yun.kugou.com/202004231204/ec400d206c48f62d424ccdf2a6becc5f/G121/M01/1A/08/GYcBAFpchDuARhf6ABcg4iPCETM478.mp3";

      //音乐播放结束后继续播放此音乐，循环不停的播放
      audio.onEnded(() => {
        that.player(wx.getBackgroundAudioManager());
      });
    },
    play() {
      if (this.flag) {
        wx.getBackgroundAudioManager().pause();
        this.flag=!this.flag
      }else{
          wx.getBackgroundAudioManager().play()
           this.flag=!this.flag
      }

      console.log();
    }
  },
  components: {}
};
</script>

<style scoped >
.icon {
       width: 1em; height: 1em;
       vertical-align: -0.15em;
       fill: currentColor;
       overflow: hidden;
    }
.color {
  background-color: blue;
}
.btn{
    display: inline-block;
  font-size: 40px;
  color: green;
    transform-origin: center center;
  animation: rotate 3s linear infinite;
}
@keyframes rotate{from{transform: rotate(0deg)}
to{transform: rotate(360deg)}
}
</style>
