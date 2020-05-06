<template>
  <view>
    <Swiper :images="images" />
    <div class="totalBox">
      <div>
        <span>{{total.num}}</span>
        <span>已报名</span>
      </div>
      <div>
        <span>{{total.poll}}</span>
        <span>总投票</span>
      </div>
      <div>
        <span>{{total.view}}</span>
        <span>浏览量</span>
      </div>
    </div>
    <button class="apply" @click="goapply()">我要报名</button>
    <div class="time">
      <Times />
    </div>

    <div class="search">
      <input type="text" class="inputText" v-model="searchVal"/>
      <input type="button" value="搜索" class="inputButton" @click="search()"/>
    </div>
    <picker @change="bindPickerChange" :value="index" :range="array">
      <view class="picker">
        {{array[index]}}
        <span class="iconfont iconxia"></span>
      </view>
    </picker>
    <ul v-for="(item, index) in list" :key="index">
      <li>
        <a @click="PlayerDetails(item.id)">
          <img :src="item.coverImg" mode="scaleToFill" />
          <span class="name">{{item.name}}</span>
          <span class="piao">{{item.ticket}}票</span>
          <button>投票</button>
        </a>
      </li>
    </ul>

    <div class="kefu">
      <div>列表</div>
      <div>关注</div>
      <div>客服</div>
    </div>
    <div class="bgmusic">
      <Bgmusic />
    </div>
  </view>
</template>
<script>
import Swiper from "@/components/swiper";
import Gohome from "@/components/gohome";
import Times from "@/components/time";
import Bgmusic from "@/components/bgmusic";

export default {
  components: { Swiper, Gohome, Times, Bgmusic },
  data() {
    return {
      images: [
        {
          url: ""
        }
      ],
      music: "",
      total: {
        num: "", //已报名
        poll: "", //总投票
        view: "" //浏览量
      },
      alllist: [],
      list: [],
      array: [
        "选择分组",
        "北大青鸟鲁广校区",
        "北大青鸟光谷校区",
        "北大青鸟光谷学院",
        "课工场华中直营总校",
        "课工场徐东校区",
        "课工场光谷校区",
        "课工场郑州兰德校区",
        "北大青鸟徐东校区"
      ],
      index: 0,
      searchVal:""
    };
  },
  beforeCreate(){
    // this.getSetting();
 
  },
  onLoad() {
     this.$fly
      .post("https://mp.zymcloud.com/hp-hd/applet/activity/list", {
        activityId: 1
        // openid:res.data
      })
      .then(res => {
        console.log(`后台交互拿回数据list:`, res);
        // 获取到后台重写的session数据，可以通过vuex做本地保存
        console.log();
        this.images[0].url = res.data.data.coverList[0].url; //banner图片渲染
        this.total.num = res.data.data.hdActivity.enroll; //已报名数据渲染
        this.total.poll = res.data.data.hdActivity.sumVote; //总票数数据渲染
        this.total.view = res.data.data.hdActivity.browse; //总浏览量数据渲染
        
      })
      .catch(err => {
        console.log(`自动请求api失败 err:`, err);
      });
  },
  mounted() {
    //获取玩家数据
    this.$fly
      .post("https://mp.zymcloud.com/hp-hd/applet/activity/activityPlayer", {
        activityId: 1
        // openid:res.data
      })
      .then(res => {
        console.table(`后台交互拿回数据activityPlayer:`, res);
        // 获取到后台重写的session数据，可以通过vuex做本地保存
        this.alllist = res.data.rows;
        this.list = res.data.rows;
      })
      .catch(err => {
        console.log(`自动请求api失败 err:`, err);
      });
  },
  methods: {
    goapply() {
      mpvue.reLaunch({
        url: "../apply/main"
      });
    },
    PlayerDetails(id){
  const url = "../PlayerDetails/main?id="+id
          wx.navigateTo({ url })
    },
    search(){
      if (!this.searchVal) {
         this.list = this.alllist
      }else{
        this.list = this.alllist.filter(element => {
          return !element.name.indexOf(this.searchVal);
        });
      }
    },
    bindPickerChange(e) {
      console.log("picker发送选择改变，携带值为", e.mp.detail.value);
      this.index = e.mp.detail.value; //groupName
      
      console.log(this.array[this.index]);

      if (this.index == 0) {
        this.list = this.alllist;
      } else {
        this.list = this.alllist.filter(element => {
          return element.groupName === this.array[this.index];
        });
      }
    }
  },
  computed: {}
};
</script>
<style>
body {
  background-color: #eee;
}
.picker {
  float: left;

  width: 50%;
  height: 30px;
  line-height: 30px;
  margin: 10px 10px;
  background-color: rgb(49, 201, 177);
  color: white;
  text-indent: 2em;
}
.picker span {
  float: right;
  margin-right: 10px;
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
.piao {
  color: rgb(49, 201, 177);
}
li button {
  margin: 10px;
  height: 30px;
  line-height: 30px;
  background-color: rgb(49, 201, 177);
}

.kefu {
  position: fixed;
  bottom: 50px;
}
.kefu div {
  background-color: rgb(225, 255, 255);
  border: 1px solid rgb(49, 201, 177);
  width: 34px;
  height: 34px;
  line-height: 34px;
  font-size: 12px;
  margin-bottom: 4px;
}
.bgmusic {
  position: fixed;
  top: 80px;
  right: 50px;
}
</style>
