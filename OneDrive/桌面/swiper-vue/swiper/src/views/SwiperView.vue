
<template>
  <section class="main">
    <!-- Main Swiper -> pass thumbs swiper instance -->
    <div class="swiper-container desktop">
       <swiper :modules="[Thumbs]" :thumbs="{ swiper:thumbsSwiper}" class="main-video" >
        <SwiperSlide
              v-for="(slideContent, index) in slides"
              :key="slideContent.id"
              :virtualIndex="index"
              watch-slides-progress 
              >
              <video controls>
                <source :src="slideContent.video" type="video/mp4">
              </video>
          </SwiperSlide>
  
      </swiper>
    </div>
    <!-- 桌機板橫式4張 -->
    <div class="swiper-container video-list-wrap desktop">
      <div class="swiper-button-prev">上一部</div>
      <swiper 
      :modules="[Thumbs, Virtual, FreeMode, Navigation]" 
      :slidesPerView="4"
      :navigation="{ 
      nextEl: '.swiper-button-next', prevEl: '.swiper-button-prev' }"
      watch-slides-progress 
      virtual
      @swiper="setThumbsSwiper"
      :spaceBetween=30
      class="video-list swiper-1">
       <swiper-slide
            v-for="(slideContent, index) in slides"
            :key="slideContent.id"
            :virtualIndex="index"
            class="video-list-slide"
            >
            <img :src="slideContent.image" alt="image">
        </swiper-slide>
      </swiper>
      <div class="swiper-button-next">下一部</div>
    </div>

    <!-- 手機板直式 -->
    <div class="swiper-container video-list-wrap mobile">
      <!-- 手機板直式 -->
      <div class="mobile-full-video" v-if="isShowMobileVideo">
          <button @click="closeVideo" class="close-btn">X</button>
          <video controls>
                 <source :src="`/video/mobile-video-${showVideoId}.mp4`" type="video/mp4">
          </video>
      </div>
      <div class="swiper-container video-list-wrap mobile" v-if="!isShowMobileVideo">
        <swiper 
          :modules="[Thumbs, Virtual, FreeMode, Navigation]" 
          :slidesPerView="1.5"
          watch-slides-progress virtual
          :spaceBetween=5 
          class="video-list mobile swiper-2"
          :breakpoints="{
            '@1.00': {
              slidesPerView:4,
              spaceBetween:5 
            }
          }"
          >

          <swiper-slide 
          v-for="(slideContent, index) in slides"
          :key="slideContent.id"
          :virtualIndex="index"
          @click="showMobileVideo(slideContent.id)"
          class="video-list-slide mobileSwiper"
            >
            <img :src="slideContent.mobile_image" alt="image" v-if="!isShowMobileVideo">
          </swiper-slide>
        </swiper>
      </div>
    </div>
  </section>
  
</template>
<script setup>
// Import Swiper Vue.js components
import { Swiper,SwiperSlide } from 'swiper/vue';
// Import Swiper styles
import 'swiper/css';
// import Swiper core and required modules
import { onMounted, ref } from 'vue'
import { Virtual, Thumbs, FreeMode,Navigation } from 'swiper';
import 'swiper/css';
import 'swiper/css/navigation';
import 'swiper/css/pagination';
import 'swiper/css/scrollbar';
// 綁定上方主螢幕ref
const thumbsSwiper = ref(null)
const setThumbsSwiper = (swiper) => {
  thumbsSwiper.value = swiper;
};
const isShowMobileVideo = ref(false)
const showVideoId = ref(null)
function showMobileVideo(id) {
  console.log("mobile-index",id)
   isShowMobileVideo.value=true
   showVideoId.value = id
}

function closeVideo() {
  isShowMobileVideo.value = false
}






//初始化swiper
onMounted(()=>{
  const swiper = document.querySelector('.main-video').swiper;

  // Now you can use all slider methods like
  console.log("main-swiper",swiper,"swiper寬度",swiper.width)
})



// 影片清單
const slides =  [
  {
  id:1,
  video: "/video/desktop-video-1.mp4",
  video_mobile: "/video/mobile-video-1.mp4",
  image: "/video/video-photo-1.png",
  mobile_image: "/video/mobile-video-photo-1.png",
},
  {
    id: 2,
    video: "/video/desktop-video-2.mp4",
    video_mobile: "/video/mobile-video-2.mp4",
    image: "/video/video-photo-2.png",
    mobile_image: "/video/mobile-video-photo-2.png",
  },
    {
    id: 3,
    video: "/video/desktop-video-3.mp4",
    video_mobile: "/video/mobile-video-3.mp4",
    image: "/video/video-photo-3.png",
    mobile_image: "/video/mobile-video-photo-3.png",
  },
    {
    id: 4,
    video: "/video/desktop-video-4.mp4",
    video_mobile: "/video/mobile-video-4.mp4",
    image: "/video/video-photo-4.png",
    mobile_image: "/video/mobile-video-photo-4.png",
  },
   {
    id: 5,
    video: "/video/desktop-video-1.mp4",
    video_mobile: "/video/mobile-video-1.mp4",
    image: "/video/video-photo-1.png",
    mobile_image: "/video/mobile-video-photo-1.png",
  },
  {
    id: 6,
    video: "/video/desktop-video-2.mp4",
    video_mobile: "/video/mobile-video-2.mp4",
    image: "/video/video-photo-2.png",
    mobile_image: "/video/mobile-video-photo-2.png",
  },
  {
    id: 7,
    video: "/video/desktop-video-3.mp4",
    video_mobile: "/video/mobile-video-3.mp4",
    image: "/video/mobile-video-photo-3.png",
  },
  {
    id: 8,
    video: "/video/desktop-video-4.mp4",
    video_mobile: "/video/mobile-video-4.mp4",
    image: "/video/mobile-video-photo-4.png",
  },
]



</script>
<style scope>
body {
  margin: 0;
}
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
.swiper-button-next,.swiper-button-prev {
 all: unset;
 height: 120px;
 width: 20px;
 background-color: #d4c7c7ba;
}
.swiper-button-next::after,.swiper-button-prev::after {
  display: none;

}
.swiper-button-prev{
  position: relative;
  right: -25%;
  top: 30%;
}
.swiper-button-next{
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
@media screen and (max-width: 800px) and (orientation: landscape) {
  .main {
    padding: 0;
  }
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
  video {
    width: 100vw;
    height: 100vh;
}
.close-btn {
  position: absolute;
  top: 15px;
  right: 15px;
  z-index: 5;
}
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
.mobile .swiper-slide-active {
  background-color: gold;
  border-radius: 8px;
  width: 100%;
  height: 100%;
}
.close-btn {
  position: absolute;
  top: 15px;
  right: 15px;
  z-index: 5;
}
.main {
  padding: 0;
}
.mobile-full-video {
  position: relative;
}
video {
  all: unset;
  width: 100vw;
  height: 100vh;
}
}



</style>