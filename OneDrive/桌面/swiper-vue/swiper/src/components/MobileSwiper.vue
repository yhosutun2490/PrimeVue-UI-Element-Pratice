<template>
  <section class="main">
   
    <!-- 手機板直式 -->
    <div class="swiper-container video-list-wrap mobile">
      <swiper :modules="[Thumbs, Virtual, FreeMode, Navigation]" :slidesPerView="1.5"
        :navigation="{ nextEl: '.swiper-button-next', prevEl: '.swiper-button-prev', }" watch-slides-progress virtual
        :spaceBetween=5 class="video-list mobile"
        observer:true
        observerParents:true
        >

        <swiper-slide v-for="(slideContent, index) in slides" :key="slideContent.id" :virtualIndex="index"
          class="video-list-slide">

          <img :src="slideContent.image" alt="image">
        </swiper-slide>
      </swiper>
    </div>
  </section>
</template>
<script setup>
// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from 'swiper/vue';
// Import Swiper styles
import 'swiper/css';
// import Swiper core and required modules
import { onMounted } from 'vue'
import { Virtual, Thumbs, FreeMode, Navigation } from 'swiper';
import 'swiper/css';
import 'swiper/css/navigation';
import 'swiper/css/pagination';
import 'swiper/css/scrollbar';
// 綁定上方主螢幕ref
// const thumbsSwiper = ref(null)
// const setThumbsSwiper = (swiper) => {
//   thumbsSwiper.value = swiper;
// };




//初始化swiper
onMounted(() => {
  const swiper = document.querySelector('.main-video').swiper;

  // Now you can use all slider methods like
  console.log("main-swiper", swiper, "swiper寬度", swiper.width)
})



// 影片清單
const slides = [
  {
    id: 1,
    video: "/video/video-photo-1.mp4",
    image: "/video/mobile-video-photo-1.png",
  },
  {
    id: 2,
    video: "/video/video-photo-2.mp4",
    image: "/video/mobile-video-photo-2.png",
  },
  {
    id: 3,
    video: "/video/video-photo-3.mp4",
    image: "/video/mobile-video-photo-3.png",
  },
  {
    id: 4,
    video: "/video/video-photo-4.mp4",
    image: "/video/video-photo-4.png",
  },
  {
    id: 5,
    video: "/video/video-photo-1.mp4",
    image: "/video/mobile-video-photo-1.png",
  },
  {
    id: 6,
    video: "/video/video-photo-2.mp4",
    image: "/video/mobile-video-photo-2.png",
  },
  {
    id: 7,
    video: "/video/video-photo-3.mp4",
    image: "/video/mobile-video-photo-3.png",
  },
  {
    id: 8,
    video: "/video/video-photo-4.mp4",
    image: "/video/video-photo-4.png",
  },
]



</script>
<style scope>
.main {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  box-sizing: border-box;
  padding: 5% 0;
}

.swiper-container {
  width: 100%;
}

.swiper {
  width: 100%;
  cursor: pointer;
}

.swiper.main-video {
  margin-bottom: 20px;
}

.video-list-wrap {
  display: flex;
}

video {
  width: 600px
}

.swiper.video-list {
  width: 550px;
  position: relative;
}

.swiper-button-next,
.swiper-button-prev {
  all: unset;
  height: 120px;
  width: 20px;
  background-color: #d4c7c7ba;
}

.swiper-button-next::after,
.swiper-button-prev::after {
  display: none;

}

.swiper-button-prev {
  position: relative;
  right: -25%;
  top: 30%;
}

.swiper-button-next {
  position: relative;
  left: -25%;
  top: 30%;
}


.swiper-slide {
  text-align: center;
  font-size: 18px;
  background: #fff;

  /* Center slide text vertically */
  display: flex;
  justify-content: center;
  align-items: center;
}

.swiper-slide img {
  display: block;
  width: 90%;
  height: 90%;
  object-fit: cover;
}

.swiper-slide-thumb-active {
  background-color: gold;
  border-radius: 8px;
  width: 100%;
  height: 100%;
}

.swiper-container.mobile {
  display: none;
}

@media screen and (max-width: 600px) {
  .swiper-container.desktop {
    display: none;
  }

  .swiper-container.mobile {
    display: block;
  }

  .swiper.video-list {
    width: 60%;
    height: 70vh;
    position: relative;
  }
}
</style>