<template>
  <view>
    <Swiper :images="images" />
    <div class="title">热门活动</div>
    <ul v-for="(item, index) in list" :key="index">
      <li>
        <a open-type="switchTab" :href="item.url">
          <span class="num">{{item.id}}</span>
        <span class="article">{{item.title}}</span>
        <span class="hot">{{item.hot}}</span>
         <icon type="success" size="20"/>
        </a>
      </li>
    </ul>
    <Gohome />
  </view>
</template>

<script>
import Swiper from "@/components/swiper";
import Gohome from "@/components/gohome";

export default {
  components: { Swiper,Gohome },
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
      list:[
        {
          id:"1",
          title:"",//活动名
          url:"../photographic/main",
          hot:"", //浏览量
          images:"https://img-oss.yunshanmeicai.com/goods/default/31d8dfa4-0d7b-4694-80f9-41b07c9d0a3a.png"
        },
         
      ]
    };
  },
  mounted() {
     this.$fly
      .post("https://mp.zymcloud.com/hp-hd/applet/activity/getActivityList", {
     
        // openid:res.data
      })
      .then(res => {
        console.log(`后台交互拿回数据getActivityList:`, res);
        // 获取到后台重写的session数据，可以通过vuex做本地保存
      
         this.list[0].hot = res.data.data[0].browse; //活动浏览量渲染 
         this.list[0].title = res.data.data[0].name; //活动名渲染 
        // this.total.num = res.data.data.hdActivity.enroll; //已报名数据渲染
        // this.total.poll = res.data.data.hdActivity.sumVote; //总票数数据渲染
        // this.total.view = res.data.data.hdActivity.browse; //总浏览量数据渲染
        // this.music = res.data.data.hdActivity.music; //总浏览量数据渲染
      })
      .catch(err => {
        console.log(`自动请求api失败 err:`, err);
      });
    

  },
  methods: {},
  computed: {}
};
</script>

<style>
body{
  background-color: #eee;
}
.title{
  margin: 10px 5px;
}
ul{
 width: 100%;
}
li{
  
  height: 50px;
  line-height: 50px;
}
.num{
  float: left;
  color: red;
  padding:0 10px;
}
.article{
  float: left;
  width: 130px;
  overflow: hidden;
text-overflow:ellipsis;
white-space: nowrap;
}
.hot{
  color: slategrey;
  padding-left: 20px;
  font-size: 14px;
}
icon{
  float: right;
 font-size: 20px;
padding-right: 20px;
}

</style>
