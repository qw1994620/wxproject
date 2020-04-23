<template>
  <view>
    <Swiper :images="images" />
    <ul >
      <li v-for="(item, index) in list" :key="index">
        <a :href="item.url">
          <img :src="item.images" mode="scaleToFill">
        <span>{{item.title}}</span>
        </a>
      </li>
    </ul>
  </view>
</template>

<script>
import Swiper from "@/components/swiper";

export default {
  components: { Swiper },
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
          title:"活动",
          url:"../activity/main",
          images:"https://img-oss.yunshanmeicai.com/goods/default/31d8dfa4-0d7b-4694-80f9-41b07c9d0a3a.png"
        },
        {
          title:"问卷",
          images:"https://img-oss.yunshanmeicai.com/goods/default/e83c8f0f-4acc-4729-bcbb-294f2b314977.jpg"
        },
        {
          title:"夏令营",
          images:"https://img-oss.yunshanmeicai.com/goods/default/e83c8f0f-4acc-4729-bcbb-294f2b314977.jpg"
        },
        {
          title:"课程",
          images:"https://img-oss.yunshanmeicai.com/goods/default/31d8dfa4-0d7b-4694-80f9-41b07c9d0a3a.png"
        }
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
ul{
 width: 100%;
 margin-top: 40px;
}
li{
  padding: 10px;
  float: left;
  width: 50%;
  height: 230px;
  text-align: center;
	list-style: none;
 
  box-sizing: border-box;
}
li a{
 background: white;
}
li a image{
  width: 100%;
  height: 167.5px;
}
li a span{
  display: inline-block;
  padding: 10px 0;
}
</style>
