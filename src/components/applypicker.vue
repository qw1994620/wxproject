<template>
  <div>
    <picker @change="bindPickerChange" :value="index" :range="array">
      <view class="picker">{{array[index]}} <span class="iconfont iconxia"></span>
      </view>
    </picker>
  </div>
</template>

<script>
export default {
  props: {},
  data() {
    return {
      array:["全部","北大青鸟鲁广校区","北大青鸟光谷校区","北大青鸟光谷学院","课工场华中直营总校","课工场徐东校区","课工场光谷校区","课工场郑州兰德校区","北大青鸟徐东校区"],
      index: 0
    };
  },
  computed: {},
  created() {},
  mounted() {},
  watch: {},
  methods: {
    bindPickerChange(e) {
      console.log("picker发送选择改变，携带值为", e.mp.detail.value);
      this.index = e.mp.detail.value;
    }
  },
  components: {}
};
</script>

<style scoped >
.picker{
   float: left;
  padding: 10px 0;
width: 65%;
background-color: honeydew;

}
span{
  float: right;
  margin-right: 10px;
}
</style>
