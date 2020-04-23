<template>
  <div>
    <div class="header">
      <img :src="imgurl" class="headimg" />
    </div>
    <div v-for="(item,index) in total" :key="index" class="totalBox">
      <div>
        <span>{{item.rank}}</span>
        <span>排名</span>
      </div>
      <div>
        <span>{{item.num}}</span>
        <span>票数</span>
      </div>
      <div>
        <span>{{item.gift}}</span>
        <span>礼物</span>
      </div>
      <div>
        <span>{{item.view}}</span>
        <span>浏览量</span>
      </div>
    </div>
    <div class="palyerDescription">
      <div class="palyerDescriptionTitle">选手描述</div>
      <div class="palyerDescriptionCon">这人很懒什么都没有留下..</div>
    </div>
    <div class="palyerDescription">
      <div class="palyerDescriptionTitle">选手照片</div>
      <img class="palyerDescriptionImg" :src="imgurl" />
    </div>
    <div class="palyerDescription">
      <div class="palyerDescriptionTitle palyerContribution">票数贡献榜</div>
      <div>
       
        <scroll-view scroll-y="true" style="height: 400rpx;" @scrolltoupper="upper" @scrolltolower="lower" @scroll="scroll" scroll-into-view="toView" scroll-top="scrollTop">
          
           <img src="https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=2572598446,712599389&fm=26&gp=0.jpg" alt="">
        </scroll-view>
      
      
      </div>
      <button type="primary" @click="gogift()">送ta礼物加票</button>
    </div>
    <div class="palyerDescription">
      <div class="palyerDescriptionTitle palyerContribution">投票记录</div>
      <ul>
        <li v-for="(item,index) in list" :key="index">
          <p class="left">
            <span>{{item.name}}</span>
            <span>{{item.time}}</span>
          </p>
          <p class="right">+{{item.num}}</p>
        </li>
      </ul>
    </div>
    <div class="footer">
      <div class="home" @click="gohome()">首页</div>
      <div class="apply" @click="apply()">投票</div>
      <div class="gift" @click="gogift()">送礼</div>
    </div>
  </div>
</template>
<script>
export default {
  props: [],
  data() {
    return {
      imgurl:
        "https://img-oss.yunshanmeicai.com/goods/default/31d8dfa4-0d7b-4694-80f9-41b07c9d0a3a.png",
      total: [
        {
          rank: "6",
          num: "20",
          gift: "1",
          view: "199"
        }
      ],
      list: [
        {
          name: "",
          time: "",
          num: ""
        }
      ]
    };
  },
  computed: {},
  created() {},
  mounted() {},
  watch: {},
  methods: {
    gohome() {
      wx.reLaunch({
        url: "../index/main"
      });
    },
    apply() {
      const myDate = new Date();
      const Y = myDate.getFullYear();
      const M = myDate.getMonth() + 1;
      const D = myDate.getDate();
      const h = myDate.getHours();
      const m = myDate.getMinutes();
      const s = myDate.getSeconds();
      var nowDate = Y + "-" + M + "-" + D + " " + h + ":" + m + ":" + s;
      this.list.push({
        name: "张三",
        time: nowDate,
        num: 1
      });
      console.log(this.list);
    },
    gogift(){
      wx.reLaunch({
        url: "../gift/main"
      });
    }
  },
  components: {}
};
</script>
<style  >
body {
  background-color: #eee;
}
.header {
  display: flex;
}
.headimg {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  margin: 20px auto;
}
.totalBox {
  margin: 20px 10px;
  height: 80px;
  background-color: rgb(49, 201, 177);
  /* line-height: 40px; */
  display: flex;
}
.totalBox div {
  flex: 1;
  display: flex;
  flex-direction: column;
  margin-top: 20px;
}
.totalBox div span {
  color: white;
  text-align: center;
}
.palyerDescription {
  margin: 10px;
  /* height: 80px; */
}
.palyerDescriptionTitle {
  height: 25px;
  text-align: center;
  background-color: white;
  margin-bottom: 2px;
}
.palyerDescriptionCon {
  background-color: white;
  height: 60px;
}
.palyerDescriptionImg {
  width: 100%;
}
.palyerContribution {
  background-color: greenyellow;
}
ul {
  margin-bottom: 60px;
}
li {
  height: 60px;
}
li .left {
  float: left;
}
li .left span {
  display: block;
  line-height: 30px;
}
li .right {
  float: right;
  line-height: 60px;
}
.footer {
  position: fixed;
  width: 100%;
  bottom: 0;
  height: 60px;
  line-height: 60px;
  display: flex;
  /* justify-content:center; */
}
.footer div {
  flex: 1;
  text-align: center;
  background-color: green;
}
.apply {
  margin: 0 1px;
}
</style>
