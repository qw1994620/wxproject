<template>
  <div>
    <div class="time">
      <p>2020-05-31 00:00:00 结束</p>
      <Times />
    </div>
    <div class="title">票数排行榜</div>
    <div class="content">
      <div class="top">
        <div class="two">
          <span class="rank">NO.2</span>
          <img :src="palyerlist[1].coverImg" alt />
          <span>{{palyerlist[1].name}}</span>
          <p>{{palyerlist[1].ticket}}票</p>
        </div>
        <div class="one">
          <span class="rank">NO.1</span>
          <img :src="palyerlist[0].coverImg" alt />
          <span>{{palyerlist[0].name}}</span>
          <p>{{palyerlist[0].ticket}}票</p>
        </div>
        <div class="three">
          <span class="rank">NO.3</span>
          <img :src="palyerlist[2].coverImg" alt />
          <span>{{palyerlist[2].name}}</span>
          <p>{{palyerlist[2].ticket}}票</p>
        </div>
      </div>
      <div v-for="(item,index) in palyerlist1" :key="index" class="bottom">
        <img :src="item.coverImg" alt />
        <div class="text">
          <span>{{item.name}}</span>
          <p>{{item.ticket}}票</p>
        </div>
        <div class="bottom-rank">{{item.ranknum}}</div>
      </div>
    </div>
  </div>
</template>
<script>
import Times from "@/components/time";
export default {
  props: [],
  data() {
    return {
      palyerlist: [
      {
        name:"",
        coverImg:"",
        ticket:""
      },
      {
        name:"",
        coverImg:"",
        ticket:""
      },
      {
        name:"",
        coverImg:"",
        ticket:""
      },
      ],
      palyerlist1:[
       
       
      ],
      
    };
  },
  computed: {

  },
  created() {},
  mounted() {
    this.$fly
      .post("https://mp.zymcloud.com/hp-hd/applet/activity/playerRank", {
        activityId: 1
        // openid:res.data
      })
      .then(res => {
        console.log(`后台交互拿回数据playerRank:`, res);
        // 获取到后台重写的session数据，可以通过vuex做本地保存
        // console.log();
        this.palyerlist=res.data.data.playerList
        this.palyerlist1=res.data.data.playerList1
         for(var i=0;i<this.palyerlist1.length;i++){
           this.palyerlist1[i].ranknum=4+i
         }
 
      })
      .catch(err => {
        console.log(`自动请求api失败 err:`, err);
      });
  },
  watch: {},
  methods: {},
  components: {
    Times
  }
};
</script>
<style  >
body {
  background-color: #eee;
}
.time {
  text-align: center;
  height: 90px;
  line-height: 40px;
}
.title {
  margin: 0 10px;
  height: 46px;
  background-color: rgb(49, 201, 178);
  text-align: center;
  line-height: 46px;
  color: white;
}
.top{
  display: flex;
  justify-content: space-around;
  text-align: center;
  margin: 20px 10px;
}
.top img{
  width: 50px;
  height: 50px;
  border-radius: 50%;
}
.top p{
  color:  rgb(49, 201, 178);
}
.two{
  display: flex;
  flex-direction: column;
  margin: 20px 0;
}
.one{
  display: flex;
  flex-direction: column;
}
.one img{
   width: 70px;
  height: 70px;
}
.three{
  display: flex;
  flex-direction: column;
  margin: 20px 0;

}
.bottom{
 display: flex;
 justify-content:space-between;
margin: 20px 30px;
}
.bottom img{
  width: 50px;
  height: 50px;
  border-radius: 50%;
}
.text{
 flex: 1;
display: flex;
flex-direction: column;
justify-content: space-around;
margin: 0 5px;
}

</style>
