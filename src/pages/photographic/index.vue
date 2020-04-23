<template>
  <view>
    
    <Swiper :images="images" />
    <div v-for="(item,index) in total" :key="index" class="totalBox">
      <div>
        <span>{{item.num}}</span>
        <span>已报名</span>
      </div>
      <div>
        <span>{{item.poll}}</span>
        <span>总投票</span>
      </div>
      <div>
        <span>{{item.view}}</span>
        <span>浏览量</span>
      </div>
    </div>
    <button class="apply" @click="goapply()">我要报名</button>
    <div class="time"><Times /></div>
    
    <div class="search">
      <input type="text" class="inputText" />
      <input type="button" value="搜索" class="inputButton" />
    </div>
     <Picker />
    <ul v-for="(item, index) in list" :key="index">
      <li>
        <a :href="item.url">
          <img :src="item.images" mode="scaleToFill" />
          <span class="name">{{item.name}}</span>
          <span class="piao">{{item.num}}票</span>
          <button>投票</button>
        </a>
      </li>
    </ul>

    <div class="kefu">
      <div>
      列表
      </div>
      <div>
        关注
      </div>
      <div>
        客服
      </div>
    </div>
    <div class="bgmusic"><Bgmusic /></div>
  </view>
</template>
<script>
import Swiper from "@/components/swiper";
import Gohome from "@/components/gohome";
import Picker from "@/components/picker";
import Times from "@/components/time";
import Bgmusic from "@/components/bgmusic";

export default {
  components: { Swiper, Gohome ,Picker,Times,Bgmusic},
  data() {
    return {
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
      
      total: [
        {
          num: "60",
          poll: "1555",
          view: "9852"
        }
      ],
      list: [
        {
          name: "张三",
          url: "../PlayerDetails/main",
          num: "99",
          images:
            "https://img-oss.yunshanmeicai.com/goods/default/31d8dfa4-0d7b-4694-80f9-41b07c9d0a3a.png"
        },
        {
          name: "李四",
          num: "88",
          images:
            "https://img-oss.yunshanmeicai.com/goods/default/e83c8f0f-4acc-4729-bcbb-294f2b314977.jpg"
        },
        {
          name: "王五",
          num: "77",
          images:
            "https://img-oss.yunshanmeicai.com/goods/default/e83c8f0f-4acc-4729-bcbb-294f2b314977.jpg"
        },
        {
          name: "老六",
          num: "66",
          images:
            "https://img-oss.yunshanmeicai.com/goods/default/31d8dfa4-0d7b-4694-80f9-41b07c9d0a3a.png"
        }
      ]
    };
  },
  methods: {
     goapply() {
    mpvue.reLaunch({
        url: '../apply/main'
    });
      
    },
     bindPickerChange(e) {
    console.log('picker发送选择改变，携带值为', e.detail.value)
    this.setData({
      index: e.detail.value
    })
  }
   
    
  },
  computed: {}
};
</script>
<style>
body {
  background-color: #eee;
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
.apply {
  margin: 10px 60px;
  background-color: rgb(49, 201, 177);
  border-radius: 8px;
  color: white;
}
.time {
  height: 40px;
  line-height: 40px;
  text-align: center;
  margin: 10px 10px;
  background-color: white;
  border-radius: 4px;
  color: #777;
}
.search {
  margin: 10px 10px;
 
}
input {
  float: left;
}
.inputText {
  width: 70%;
  background-color: white;
   height: 46px;
}
.inputButton {
  width: 30%;
  background-color: rgb(49, 201, 177);
  color: white;
   height: 46px;
   line-height: 46px;
}
.change {
  float: left;
  width: 50%;
  height: 30px;
  line-height: 30px;
  margin: 10px 10px;
  background-color: rgb(49, 201, 177);
  color: white;
}
ul {
  width: 100%;
  margin-top: 40px;
}
li {
  padding: 10px;
  float: left;
  width: 50%;
  height: 280px;
  list-style: none;
  box-sizing: border-box;
}
li a {
  background: white;
  display: inline-block;
  width: 100%;
  height: 100%;
}
li a image {
  width: 100%;
  height: 167.5px;
}
li a span {
  display: block;
  margin-left: 10px;
}
.piao{
  color: rgb(49, 201, 177)
}
li button{
  margin: 10px;
  height: 30px;
  line-height: 30px;
  background-color: rgb(49, 201, 177);
}

.kefu{
  position: fixed;
  bottom: 50px;
}
.kefu div{
  background-color: rgb(225, 255, 255);
  border: 1px solid rgb(49, 201, 177);
  width: 34px;
  height: 34px;
  line-height: 34px;
  font-size: 12px;
margin-bottom: 4px;
}
.bgmusic{
  position: fixed;
  top: 80px;
  right: 50px;
}
</style>
