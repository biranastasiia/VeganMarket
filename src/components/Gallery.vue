<template>
  <swiper
    :spaceBetween="10"
    :thumbs="{ swiper: thumbsSwiper }"
    :modules="modules"
    class="gallery-swiper__main"
  >
    <swiper-slide v-for="image in list" :key="image">
      <div class="gallery__image-wrap">
        <div class="gallery__image-signs">
          <div class="gallery__image-sign discount" v-if="discount">sale</div>
          <div class="gallery__image-sign new" v-if="is_new">new</div>
        </div>
        <img :src="image" :alt="title" />
      </div>
    </swiper-slide>
  </swiper>
  <swiper
    @swiper="setThumbsSwiper"
    :spaceBetween="10"
    :slidesPerView="4"
    :freeMode="true"
    :watchSlidesProgress="true"
    :modules="modules"
    :direction="'vertical'"
    class="gallery-swiper__thumb"
  >
    <swiper-slide v-for="image in list" :key="image">
      <img :src="image" :alt="title" />
    </swiper-slide>
  </swiper>
</template>

<script>
import { ref } from 'vue'
import { Swiper, SwiperSlide } from 'swiper/vue'
import 'swiper/css'
import 'swiper/css/free-mode'
import 'swiper/css/navigation'
import 'swiper/css/thumbs'
import { FreeMode, Navigation, Thumbs } from 'swiper/modules'

export default {
  props: ['list', 'title', 'discount', 'is_new'],
  components: {
    Swiper,
    SwiperSlide
  },
  setup() {
    const thumbsSwiper = ref(null)
    const setThumbsSwiper = (swiper) => {
      thumbsSwiper.value = swiper
    }

    return {
      thumbsSwiper,
      setThumbsSwiper,
      modules: [FreeMode, Navigation, Thumbs]
    }
  }
}
</script>
