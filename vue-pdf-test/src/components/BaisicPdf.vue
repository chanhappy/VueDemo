<template>
  <vue-seamless-scroll class="seamless-warp" id="scroll_in2">
    <pdf v-for="item in pageTotal" :src="pdfUrl" :key="item" :page="item"> </pdf>
  </vue-seamless-scroll>
</template>

<script>
import pdf from "vue-pdf";
import vueSeamlessScroll from "vue-seamless-scroll";

export default {
  components: {
    pdf,
    vueSeamlessScroll,
  },
  data() {
    return {
      pageTotal: 0,
      pdfUrl: "./ccc.pdf",
      timer: "",
      isStop: true,
    };
  },
  mounted() {
    this.autoSroll("scroll_in2");
    this.getTotal();
  },
  destroyed() {
    clearInterval(this.timer);
  },
  methods: {
    getTotal() {
      this.pdfUrl = pdf.createLoadingTask(this.pdfUrl);
      // 获取页码
      this.pdfUrl.promise.then((pdf) => (this.pageTotal = pdf.numPages));
    },
    autoSroll(id) {
      // isStop 为true时停止滚动
      this.isStop = false;
      var h = -1;
      this.timer = setInterval(function () {
        this.isStop = true;
        //获取当前滚动条高度
        var current = document.getElementById(id).scrollTop;
        if (current == h) {
          //滚动到底端,返回顶端
          h = 0;
          document.getElementById(id).scrollTop = h + 2;
        } else {
          //以25ms/3.5px的速度滚动
          h = current;
          document.getElementById(id).scrollTop = h + 2;
        }
      }, 50);
    },
  },
};
</script>
<style>
.seamless-warp {
  height: 600px;
  overflow: hidden;
}
</style>
