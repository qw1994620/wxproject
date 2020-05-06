<template>
    <div>
        <div><img src="https://img-oss.yunshanmeicai.com/goods/default/e83c8f0f-4acc-4729-bcbb-294f2b314977.jpg" alt=""></div>
        <div class="text"><p>您好!</p><br><p class="con">感谢您对武汉鸿鹏教育的支持与信任.我们将秉承教育改变生活的理念,我们将秉承教育改变生活的理念我们将秉承教育改变生活的理念我们将秉承教育改变生活的理念</p></div>
        <button type="primary" @click="start()">开始问卷调查</button>
    </div>
</template>

<script>
export default {
    props: [

    ],
    data() {
        return {

        };
    },
    computed: {

    },
    created() {

    },
    mounted() {

    },
    watch: {

    },
    methods: {
start(){
    wx.reLaunch({
        url: '../question1/main',
        
    });
      
}
    },
    components: {

    },
};
</script>

<style scoped >
img{
    width: 100%;
}
.text{
    margin: 16px;
    padding: 16px;
    border: 1px solid black;
    border-radius: 6px;
}
.con{
    text-indent: 2em;
}
button{
    width: 40%;
}
</style>
