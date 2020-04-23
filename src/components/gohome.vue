<template>
  <div>
    <a @click="gohome()">首页</a>
  </div>
</template>
<script>
export default {
  props: {
    
  },
  data() {
    return {
      indicatorDots: true,
      autoplay: true,
      interval: 3000,
      duration: 500
    };
  },
  methods: {
    gohome() {
    mpvue.reLaunch({
        url: '../index/main'
    });
    }
  }
};
</script>
<style scoped>
a {
    position: fixed;
    right: 10px;
    bottom: 50px;
  width: 40px;
  height: 40px;
  line-height: 40px;
  text-align: center;
  font-size: 12px;
  border-radius: 20px;
  background-color: rgb(186, 232, 253);
  border: 1px solid #d5d5d5;
  color: rgb(132, 209, 245);
}
</style>
