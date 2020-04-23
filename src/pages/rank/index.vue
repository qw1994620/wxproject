<template>
  <div>
    <div class="time">
      <p>2020-05-31 00:00:00 结束</p>
      <Times />
    </div>
    <div class="title">票数排行榜</div>
    <div class="content">
      <div v-for="(item,index) in palyer" :key="index">
        <img :src="item.img" alt />
        <div>
          <span>{{item.name}}</span>
          <p>{{item.applynum}}票</p>
        </div>
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
      palyer: [
        {
          name: "令狐冲",
          img:
            "http://img1.imgtn.bdimg.com/it/u=2047220947,3490962718&fm=26&gp=0.jpg",
          applynum: "4396"
        },
        {
          name: "张无忌",
          img:
            "http://img1.imgtn.bdimg.com/it/u=2047220947,3490962718&fm=26&gp=0.jpg",
          applynum: "4396"
        },
        {
          name: "小鱼儿",
          img:
            "http://img1.imgtn.bdimg.com/it/u=2047220947,3490962718&fm=26&gp=0.jpg",
          applynum: "4396"
        },
        {
          name: "小鱼儿",
          img:
            "http://img1.imgtn.bdimg.com/it/u=2047220947,3490962718&fm=26&gp=0.jpg",
          applynum: "4396"
        },
        {
          name: "小鱼儿",
          img:
            "http://img1.imgtn.bdimg.com/it/u=2047220947,3490962718&fm=26&gp=0.jpg",
          applynum: "4396"
        },
        {
          name: "小鱼儿",
          img:
            "http://img1.imgtn.bdimg.com/it/u=2047220947,3490962718&fm=26&gp=0.jpg",
          applynum: "4396"
        },
        {
          name: "小鱼儿",
          img:
            "http://img1.imgtn.bdimg.com/it/u=2047220947,3490962718&fm=26&gp=0.jpg",
          applynum: "4396"
        },
        {
          name: "小鱼儿",
          img:
            "http://img1.imgtn.bdimg.com/it/u=2047220947,3490962718&fm=26&gp=0.jpg",
          applynum: "4396"
        },
        {
          name: "小鱼儿",
          img:
            "http://img1.imgtn.bdimg.com/it/u=2047220947,3490962718&fm=26&gp=0.jpg",
          applynum: "4396"
        },
        {
          name: "小鱼儿",
          img:
            "http://img1.imgtn.bdimg.com/it/u=2047220947,3490962718&fm=26&gp=0.jpg",
          applynum: "4396"
        }
      ]
    };
  },
  computed: {},
  created() {},
  mounted() {
   
  },
  watch: {},
  methods: {
   
  },
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
.content {
  display: flex;
  margin: 10px;
  justify-content: space-between;
  flex-flow: wrap;
}
.content div:nth-child(-n + 3) {
  width: 30%;
  display: flex;
  flex-direction: column;
  text-align: center;
}
.content div:nth-child(-n + 3) div {
  width: 100%;
}
.content div:nth-child(-n + 3) img {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  margin: 10px auto;
}
.content div:nth-child(-n + 3) p {
  color: rgb(49, 201, 178);
}

.content div:nth-child(n + 4) {
  margin: 0 10px;
  width: 100%;
  display: flex;
}
.content div:nth-child(n + 4) img {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  margin: 10px 0;
}

.content div:nth-child(n + 4) div {
  display: flex;
  flex-flow: column;
  justify-content: space-around;
}
</style>
