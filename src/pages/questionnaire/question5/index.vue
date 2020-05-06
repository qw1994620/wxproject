<template>
  <div>
    <div>
      <img
        src="https://img-oss.yunshanmeicai.com/goods/default/e83c8f0f-4acc-4729-bcbb-294f2b314977.jpg"
        alt
      />
    </div>
    <h2>当前第5题/共8题</h2>
    <div class="title">{{question}}</div>
    <div>
      <textarea class="textarea"  :value="text" placeholder="请提出您宝贵的意见"></textarea >
    </div>
    <button type="primary" @click="next()">下一题</button>
  </div>
</template>

<script>
export default {
  props: [],
  data() {
    return {
      question:"意见",
      text:""
           
        
      
    };
  },
  computed: {},
  created() {},
  mounted() {},
  watch: {},
  methods: {
    checkboxChange(e) {
      console.log("radio发生change事件，携带value值为：", e.mp.detail.value);
    },
    next(){
        wx.reLaunch({
            url: '../question6/main',
           
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
.textarea{
  border: 1px solid #eee;
  padding: 10px;
  margin: 20px;
}
button{
    width: 40%;
}
</style>
