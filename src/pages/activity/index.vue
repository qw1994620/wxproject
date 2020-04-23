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
          title:"宏鹏教育程序员美丽XXXXXXXXXX",
          url:"../photographic/main",
          hot:"6698",
          images:"https://img-oss.yunshanmeicai.com/goods/default/31d8dfa4-0d7b-4694-80f9-41b07c9d0a3a.png"
        },
          {
          id:"2",
          title:"宏鹏教育程序员美丽XXXXXXXXXX",
          url:"../activity/main",
          hot:"6698",
          images:"https://img-oss.yunshanmeicai.com/goods/default/31d8dfa4-0d7b-4694-80f9-41b07c9d0a3a.png"
        },  {
          id:"3",
          title:"宏鹏教育程序员美丽XXXXXXXXXX",
          url:"../activity/main",
          hot:"6698",
          images:"https://img-oss.yunshanmeicai.com/goods/default/31d8dfa4-0d7b-4694-80f9-41b07c9d0a3a.png"
        },  {
          id:"4",
          title:"宏鹏教育程序员美丽XXXXXXXXXX",
          url:"../activity/main",
          hot:"6698",
          images:"https://img-oss.yunshanmeicai.com/goods/default/31d8dfa4-0d7b-4694-80f9-41b07c9d0a3a.png"
        },
      ]
    };
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
