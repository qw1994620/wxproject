<template>
  <div>
    <p>剩余{{day}}天 {{h}}时 {{m}}分 {{s}}秒</p>
  </div>
</template>

<script>
export default {
  props: [],
  data() {
    return {
      day: "",
      h: "",
      m: "",
      s: ""
    };
  },
  computed: {},
  created() {},
  mounted() {
        this.gettDate();
  },
  watch: {},
  methods: {
       gettDate() {
      var now = +new Date();
      // 拿到2019-11-11的毫秒数  把结束的时间换算成毫秒数
      var end = +new Date("2020-05-30:00:00:00");
      var midden = end - now; //毫秒数
      var middenS = midden / 1000; // 秒
      // 假设 1000s /60/60/24
      this.day = parseInt(middenS / 60 / 60 / 24); //天
      //   console.log(day);
      this.h = parseInt((middenS / 60 / 60) % 24); //小时
      //   console.log(h);
      // 50 小时 % 24 === 2  2天2小时
      this.m = parseInt((middenS / 60) % 60);
      //   console.log(m);
      this.s = parseInt(middenS % 60);
      //   console.log(s);
      const that = this;
      setTimeout(function() {
        that.gettDate();
      }, 1000);
    }
  },
  components: {}
};
</script>

<style scoped >
</style>
