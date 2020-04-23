<template>
  <div>
    <div class="title">在线报名</div>
    <form action="#">
      <label for="username">
        <span>选手名称</span>
        <input
          class="weui-input"
          maxlength="5"
          placeholder="请输入选手名称"
          id="username"
          v-model="username"
        />
      </label>
      <label for="usernum">
        <span>选手名称</span>
        <input
          class="weui-input"
          maxlength="11"
          placeholder="请输入手机号"
          id="usernum"
          v-model="usernum"
        />
      </label>
      <label for="grouping">
        <span>分组</span>
        <Applypicker />
      </label>
      <label for="description">
        <span>分组</span>
        <textarea @blur="bindTextAreaBlur" placeholder="选手描述" />
      </label>
      <Upload width="120rpx" height="120rpx" max="3" @choosed="choosed"></Upload>
      <button formType="submit" type="primary" @click="submit()">提交</button>
    </form>
  </div>
</template>

<script>
import Applypicker from "@/components/applypicker";
import Upload from "@/components/upload";
export default {
  props: [],
  data() {
    return {
      images: [],
      username: "",
      usernum: ""
    };
  },
  computed: {},
  created() {},
  mounted() {},
  watch: {},
  methods: {
    submit() {
      console.log(this.username);
      const testName = /^(?:[\u4e00-\u9fa5·]{2,16})$/;
      const testNum = /^(?:(?:\+|00)86)?1(?:(?:3[\d])|(?:4[5-7|9])|(?:5[0-3|5-9])|(?:6[5-7])|(?:7[0-8])|(?:8[\d])|(?:9[1|8|9]))\d{8}$/;

      console.log();
      if (!testName.test(this.username)) {
        wx.showToast({
          title: "请填写正确的姓名格式",
          icon: "none",
          duration: 3000
        });
      } else if (!testNum.test(this.usernum)) {
        wx.showToast({
          title: "请输入正确的手机号",
          icon: "none",
          duration: 3000
        });
      }
    }
  },
  components: {
    Applypicker,
    Upload
  }
};
</script>

<style scoped >
body {
  background-color: #eee;
}
.title {
  text-align: center;
  font-size: 20px;
  font-weight: 900;
  color: green;
  padding: 20px 0;
}
label {
  display: block;
  overflow: hidden;
  /* background-color: green; */
  /* height: 40px; */
  margin-bottom: 10px;
}
span {
  /* padding: 10px 0; */
  float: left;
  width: 30%;
  padding-left: 10px;
  box-sizing: border-box;
  font-size: 16px;
  line-height: 40px;
}
textarea {
  height: 130px;
  float: left;
  width: 65%;
  background-color: honeydew;
}
input {
  float: left;
  padding: 10px 0;
  width: 65%;
  background-color: honeydew;
}
button {
  margin: 0 20px;
}
</style>
