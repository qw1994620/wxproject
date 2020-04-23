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
      <div class="gift">
      <div class="title">送礼物加票数</div>
      
        <ul class="giftDescriptionCon">
          <li v-for="(item,index) in giftlist"  :key="index"><span class="giftTitle">{{item.title}}</span><img mode="scaleToFill" class="giftImg" :src="item.img" alt=""><span class="giftNum">+{{item.num}}票</span></li>
        </ul>
      
    </div>
    <div class="numChange">
      <div class="numChange-left"> <span>&yen; {{gifttotal}}</span>  <span>&nbsp;+{{applynum}}票</span></div>
      <div class="numChange-right"><button size="mini" @click="sub()">-</button><span>{{giftnum}}</span><button size="mini" @click="add()">+</button></div>
    </div>
    <button class="submit" type="primary">立即送出</button>
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
      giftlist:[
        {
          title:"棒棒糖",
          img:"https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1587536142297&di=207586865b7059209f19e91e3c75e218&imgtype=0&src=http%3A%2F%2Fdpic.tiankong.com%2Fiz%2F3g%2FQJ6501147050.jpg",
          num:"20"
        },
        {
          title:"棒棒糖",
          img:"https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1587536142297&di=207586865b7059209f19e91e3c75e218&imgtype=0&src=http%3A%2F%2Fdpic.tiankong.com%2Fiz%2F3g%2FQJ6501147050.jpg",
          num:"20"
        },
        {
          title:"棒棒糖",
          img:"https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1587536142297&di=207586865b7059209f19e91e3c75e218&imgtype=0&src=http%3A%2F%2Fdpic.tiankong.com%2Fiz%2F3g%2FQJ6501147050.jpg",
          num:"20"
        },
        {
          title:"棒棒糖",
          img:"https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1587536142297&di=207586865b7059209f19e91e3c75e218&imgtype=0&src=http%3A%2F%2Fdpic.tiankong.com%2Fiz%2F3g%2FQJ6501147050.jpg",
          num:"20"
        },
        {
          title:"棒棒糖",
          img:"https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1587536142297&di=207586865b7059209f19e91e3c75e218&imgtype=0&src=http%3A%2F%2Fdpic.tiankong.com%2Fiz%2F3g%2FQJ6501147050.jpg",
          num:"20"
        },
        {
          title:"棒棒糖",
          img:"https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1587536142297&di=207586865b7059209f19e91e3c75e218&imgtype=0&src=http%3A%2F%2Fdpic.tiankong.com%2Fiz%2F3g%2FQJ6501147050.jpg",
          num:"20"
        },
      ],
      giftnum:1,
      gifttotal:6,
    applynum:20
    };
  },
  computed: {},
  created() {},
  mounted() {},
  watch: {},
  methods: {
    sub(){
      if(this.giftnum>1){
        
        
        this.giftnum--
        this.gifttotal=this.giftnum*6
  this.applynum=this.giftnum*20
        
      }
    },
    add(){
      if(this.giftnum<99){
       this.giftnum++
        this.gifttotal=this.giftnum*6
  this.applynum=this.giftnum*20
      }
    }
  },
  components: {}
};
</script>

<style >
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
.gift{
  margin: 10px;
}
.title {
  height: 25px;
  text-align: center;
  background-color: white;
  margin-bottom: 2px;
}
.giftDescriptionCon{
display: flex;
width: 100%;
 flex-wrap: wrap;
 justify-content:space-between;
 
}
.giftDescriptionCon li{
  width: 30%;
  text-align: center;
  margin: 30px 0;
  height: 110px;
}
.giftTitle{

}
.giftImg{
width: 100%;
  height: 100%;
  
}
.giftNum{
  background-color: greenyellow;
display: block;
}
.numChange{
  margin: 20px 10px 50px 10px;
  height: 40px;
  line-height: 40px;
}
.numChange-left{
  float: left;
}
.numChange-right{
  float: right;
}
.numChange-right button{
  top:8px;
}
.submit{
  width: 100%;
  position: fixed;
  bottom: 0;
}
</style>
