<template>
  <div>
    <p>Amazin swiper huh? 😄</p>
    <swiper :options="swiperOptions" class="swiper">
      <swiper-slide v-for="image in gallery" :key="image.id">
        <img :src="image.src" />
      </swiper-slide>

      <div
        v-show="prevSlideAvailable"
        slot="button-prev"
        @click="$refs.swiper.$swiper.slidePrev()"
      ></div>
      <div
        v-show="nextSlideAvailable"
        slot="button-next"
        @click="$refs.swiper.$swiper.slideNext()"
      ></div>
    </swiper>
  </div>
</template>

<script>
import { Swiper, SwiperSlide } from 'vue-awesome-swiper'
import 'swiper/swiper-bundle.css'

export default {
  name: 'AwesomeSwiper',
  components: {
    Swiper,
    SwiperSlide,
  },
  data() {
    return {
      gallery: [
        { id: 1, src: 'https://source.unsplash.com/random/500x500?sig=1' },
        { id: 2, src: 'https://source.unsplash.com/random/500x500?sig=2' },
        { id: 3, src: 'https://source.unsplash.com/random/500x500?sig=3' },
      ],
      swiperOptions: {
        slidesPerView: 1,
        spaceBetween: 30,
        lazy: false,
        effect: 'fade',
        pagination: {
          el: '.swiper-pagination',
          type: 'progressbar',
        },
        navigation: {
          disabledClass: '.nice-meme',
          nextEl: '.swiper-button-next',
          prevEl: '.swiper-button-prev',
        },
      },
    }
  },
}
</script>

<style scoped>
.swiper {
  width: 500px;
  margin: 0 auto;
}
</style>
