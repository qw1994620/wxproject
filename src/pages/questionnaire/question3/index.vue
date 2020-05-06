<template>
  <div>
    <div>
      <img
        src="https://img-oss.yunshanmeicai.com/goods/default/e83c8f0f-4acc-4729-bcbb-294f2b314977.jpg"
        alt
      />
    </div>
    <h2>当前第3题/共8题</h2>
    <div class="title">{{list.question}}</div>
    <div>
      <radio-group class="radio-group" @change="radioChange">
        <radio
          class="radio"
          v-for="(item,index) in list.answer"
          :key="index"
          :value="item.name"
          :checked="item.checked"
        >
          <text>{{item.name}}</text>
        </radio>
      </radio-group>
    </div>
    <button type="primary" @click="next()">下一题</button>
  </div>
</template>

<script>
export default {
  props: [],
  data() {
    return {
      list: {
        question: "1.你选择学习的课程是?(单选)",
        answer: [
          {
            name: "A.软件工程师",
            checked: true
          },
          {
            name: "B.ACCP",
            checked: false
          },
          {
            name: "C.北美大数据工程师",
            checked: false
          },
          {
            name: "D.JAVA中级程序员",
            checked: false
          },
          {
            name: "E.互联网架构师",
            checked: false
          },
          {
            name: "F.Web前端工程师",
            checked: false
          },
          {
            name: "G.UI设计师",
            checked: false
          },
          {
            name: "H.互联网架构师",
            checked: false
          },
          {
            name: "I.互联网架构师",
            checked: false
          }
        ]
      }
    };
  },
  computed: {},
  created() {},
  mounted() {},
  watch: {},
  methods: {
    radioChange(e) {
      console.log("radio发生change事件，携带value值为：", e.mp.detail.value);
    },
    next(){
        wx.reLaunch({
            url: '../question4/main',
           
        });
          
    }
  },
  components: {}
};
</script>

<style scoped >
img{
    width: 100%;
}
.title{
    font-size: 18px;
    font-weight: 900;
}
.radio-group{
    margin: 20px 20px;
}
.radio{
    display: flex;
    border: 1px solid #eee;
    line-height: 40px;
    padding: 0 10px;
}
button{
    width: 40%;
}
</style>
