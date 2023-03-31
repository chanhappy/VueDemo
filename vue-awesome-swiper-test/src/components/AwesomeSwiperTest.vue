<template>
  <div>
    <swiper :options="swiperOption" class="swiper">
      <swiper-slide v-for="(item, index) in images" :key="index">
        <img :src="item.url" alt="" />
      </swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>
</template>
<script>
import { swiper, swiperSlide } from "vue-awesome-swiper";
import "swiper/dist/css/swiper.css";

export default {
  name: "vue-awesome-swiper-test",
  components: {
    swiper,
    swiperSlide,
  },
  data() {
    return {
      swiperOption: {
        autoplay: {
            delay: 1000, // 设置每屏滑动的时间间隔为3秒
        },
        // speed: 1000, // 滑动速度，即slider自动滑动开始到结束的时间（单位ms）
        loop: true, // 是否循环播放
        autoplayDisableOnInteraction: false, // 手动滑动后是否禁止autoplay
        pagination: {
          el: ".swiper-pagination",
          clickable: true,
        },
      },
      images: [
        { url: "./../assets/1.jpg" },
        { url: "./../assets/2.jpg" },
        { url: "./../assets/3.jpg" },
      ],
    };
  },
};
</script>
<style>
.swiper-container {
  width: 500px;
  height: 300px;
}

img {
  width: 500px;
  height: 300px;
  background: red;
}
</style>
