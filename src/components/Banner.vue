<template>
  <section class="banner">
    <swiper
      :slides-per-view="1"
      :space-between="0"
      :autoplay="{ delay: 4000 }"
      :loop="true"
      :speed="1000"
      :modules="modules"
      :pagination="{
        clickable: true
      }"
    >
      <swiper-slide>
        <div class="container">
          <div class="banner__slide-inner">
            <div class="banner__content">
              <div class="banner__subtitle">just from the garden</div>
              <h1 class="banner__title">create a unique plate filled with fresh vegetables</h1>
              <p class="banner__text">
                Lorem ipsum dolor sit amet consectetur adipisicing elit. Quae vitae corrupti tenetur
                sapiente rem repellendus deleniti sit blanditiis consectetur nulla.
              </p>
              <div class="banner__button cta-button" @click="scrollToBlock()">Go Shopping</div>
            </div>
            <div class="banner__image">
              <img src="../assets/images/backgrounds/salad.jpg" alt="plate" />
            </div>
          </div>
        </div>
      </swiper-slide>
      <swiper-slide>
        <div class="container">
          <div class="banner__slide-inner">
            <div class="banner__content">
              <div class="banner__subtitle">just from the garden</div>
              <h2 class="banner__title">add spices and nuts to your diet</h2>
              <p class="banner__text">
                Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolorum voluptatum nobis
                veniam, suscipit, excepturi, molestiae dolorem perferendis iusto perspiciatis dolor
                quaerat similique debitis sunt eveniet modi incidunt.
              </p>
              <div class="banner__button cta-button" @click="scrollToBlock()">Go Shopping</div>
            </div>
            <div class="banner__image">
              <img src="../assets/images/backgrounds/spices.jpg" alt="spices" />
            </div>
          </div>
        </div>
      </swiper-slide>
      <swiper-slide>
        <div class="container">
          <div class="banner__slide-inner">
            <div class="banner__content">
              <div class="banner__subtitle">just from the garden</div>
              <h2 class="banner__title">Maintain your health by eating healthy food</h2>
              <p class="banner__text">
                Lorem ipsum dolor sit amet consectetur adipisicing elit. Libero, dolores sed!
                Expedita nobis hic earum autem? Tenetur accusamus porro quis eveniet perferendis
                ullam cupiditate nisi veniam!
              </p>
              <div class="banner__button cta-button" @click="scrollToBlock()">Go Shopping</div>
            </div>
            <div class="banner__image">
              <img src="../assets/images/backgrounds/cooking.jpg" alt="cooking" />
            </div>
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
