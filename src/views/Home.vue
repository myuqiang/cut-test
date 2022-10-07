<template>
  <div class="home">
    <div id="ddd">
      <div class="print" @click="generatorImage" style="margin-bottom:20px">
      <button>保存图片</button>
    </div>
    <div class="content" ref="addImage">
      <div ref="capture" >
           需要保存的html片段
           <!-- <img alt="Vue logo" src="../assets/logo.png" />
          <HelloWorld msg="Welcome to Your Vue.js App" /> -->
          <EchartsDemo />
      </div>
    </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";
import EchartsDemo from "@/components/Echarts.vue";
import  html2canvas  from  'html2canvas'

export default {
  name: "Home",
  components: {
    // HelloWorld,
    EchartsDemo
  },
  data() {
    return {
     
    }
  },
  mounted() {
    // 接收domain1的数据
    window.addEventListener('message',(e) => {
        console.log('iframe',e.data);
    
        if(e.origin !== 'http://local.chanjue.top:1024')
        return;
    
        // 发送消息给domain1
        window.parent.postMessage('来自domain2的消息', e.origin);
    }, false);
  },
  methods: {
    generatorImage() {
      html2canvas(this.$refs.capture).then(canvas => {
        // this.$refs.addImage.append(canvas);//在下面添加canvas节点
        let link = document.createElement("a");
        link.href = canvas.toDataURL();//下载链接
        link.setAttribute("download","截取的html片段.png");
        link.style.display = "none";//a标签隐藏
        document.body.appendChild(link);
        link.click();
      });
    },
  }
};
</script>
