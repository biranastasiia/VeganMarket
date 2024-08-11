<template>
  <section class="banner">
    <swiper
      :slides-per-view="1"
      :space-between="0"
      :loop="true"
      :autoplay="{ delay: 5000 }"
      :speed="1500"
      :modules="modules"
      :pagination="{
        clickable: true
      }"
    >
      <swiper-slide>
        <div class="container">
          <div class="banner__content">
            <h1 class="banner__title">Fresh Food Market</h1>
            <p class="banner__text">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Eius, veritatis explicabo
              necessitatibus mollitia nostrum eos nisi quo similique vero aut delectus labore
              assumenda quis reprehenderit exercitationem maxime harum quae deleniti.
            </p>
            <div class="banner__button cta-button" @click="scrollToBlock()">Go Shopping!</div>
          </div>
        </div>
      </swiper-slide>
      <swiper-slide>
        <div class="container">
          <div class="banner__content">
            <h2 class="banner__title">Fresh Food Market</h2>
            <p class="banner__text">
              Lorem ipsum dolor, sit amet consectetur adipisicing elit. Corporis veritatis iste
              optio explicabo dolorem quo quis neque ad eaque quasi?
            </p>
            <div class="banner__button cta-button" @click="scrollToBlock()">Go Shopping!</div>
          </div>
        </div>
      </swiper-slide>
      <swiper-slide>
        <div class="container">
          <div class="banner__content">
            <h2 class="banner__title">Fresh Food Market</h2>
            <p class="banner__text">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Libero, dolores sed! Expedita
              nobis hic earum autem? Tenetur accusamus porro quis eveniet perferendis ullam
              cupiditate nisi veniam! Similique voluptates ducimus quis!
            </p>
            <div class="banner__button cta-button" @click="scrollToBlock()">Go Shopping!</div>
          </div>
        </div>
      </swiper-slide>
    </swiper>
  </section>
</template>

<script>
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Autoplay, Pagination } from 'swiper/modules'
import 'swiper/css'
import 'swiper/css/pagination'

export default {
  components: {
    Swiper,
    SwiperSlide
  },
  setup() {
    return {
      modules: [Autoplay, Pagination]
    }
  },
  methods: {
    scrollToBlock() {
      const block = document.querySelector('.top-products')
      block.scrollIntoView({ behavior: 'smooth', block: 'start', inline: 'nearest' })
    }
  }
}
</script>
