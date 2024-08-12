<template>
  <swiper
    :autoplay="{ delay: 5000 }"
    :modules="modules"
    :navigation="nav"
    :slidesPerView="1"
    :spaceBetween="20"
    :breakpoints="{
      '640': {
        slidesPerView: 2
      },
      '768': {
        slidesPerView: 3
      },
      '1024': {
        slidesPerView: 5
      }
    }"
  >
    <swiper-slide v-for="product in productsList" :key="product.id">
      <ProductCard :data="product" />
    </swiper-slide>
  </swiper>
</template>

<script>
import axios from 'axios'
import ProductCard from './ProductCard.vue'
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Autoplay, Navigation } from 'swiper/modules'
import 'swiper/css'
import 'swiper/css/navigation'

export default {
  props: ['nav'],
  components: {
    ProductCard,
    Swiper,
    SwiperSlide
  },
  setup() {
    return {
      modules: [Autoplay, Navigation]
    }
  },
  data() {
    return {
      productsList: {}
    }
  },
  mounted() {
    this.getProductsList()
  },
  methods: {
    getProductsList() {
      const self = this
      //   this.loader = true

      axios
        .get('/mocks/productsList.json')
        .then(function (response) {
          self.productsList = response.data
          //   self.loader = false
        })
        .catch(function (error) {
          console.log(error, 'error')
          //   self.loader = false
        })
    }
  }
}
</script>
