<template>
  <main>
    <Banner />
    <section class="section">
      <div class="container">
        <div class="section__gallery">
          <div class="section__gallery-column">
            <div class="section__image-1">
              <img src="../assets/images/backgrounds/diet_3.png" alt="healthy food" />
            </div>
          </div>
          <div class="section__gallery-column">
            <div class="section__image-2">
              <img src="../assets/images/backgrounds/diet_1.jpg" alt="healthy food" />
            </div>
            <div class="section__image-3">
              <img src="../assets/images/backgrounds/diet_2.png" alt="healthy food" />
            </div>
          </div>
        </div>
        <div class="section__content">
          <div class="section__subtitle">About healthy diet</div>
          <h2 class="section__title">Food is an important<br />part Of a balanced Diet</h2>
          <p class="section__text">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque diam pellentesque
            bibendum non dui volutpat fringilla bibendum. Urna, elit augue urna, vitae feugiat
            pretium donec id elementum. Ultrices mattis vitae mus risus. Lacus nisi, et ac dapibus
            sit eu velit in consequat.
          </p>
          <div class="cta-button">Show more</div>
        </div>
      </div>
    </section>
    <section class="benefits">
      <div class="container">
        <h2 class="section__title">Why Choose us?</h2>
        <p class="section__text">
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque diam pellentesque
          bibendum non dui volutpat fringilla bibendum.
        </p>
        <div class="benefits__list">
          <div class="benefits__item">
            <div class="benefits__item-icon">
              <img src="../assets/images/icons/truck.svg" alt="truck" />
            </div>
            <div class="benefits__item-body">
              <div class="benefits__item-title">Fast Delivery</div>
              <p class="benefits__item-text">
                Lorem ipsum dolor sit amet consectetur adipisicing elit.
              </p>
            </div>
          </div>
          <div class="benefits__item">
            <div class="benefits__item-icon">
              <img src="../assets/images/icons/hamburger.svg" alt="hamburger" />
            </div>
            <div class="benefits__item-body">
              <div class="benefits__item-title">Fresh food</div>
              <p class="benefits__item-text">
                Lorem ipsum dolor sit amet consectetur adipisicing elit.
              </p>
            </div>
          </div>
          <div class="benefits__item">
            <div class="benefits__item-icon">
              <img src="../assets/images/icons/timer.svg" alt="timer" />
            </div>
            <div class="benefits__item-body">
              <div class="benefits__item-title">24/7 services</div>
              <p class="benefits__item-text">
                Lorem ipsum dolor sit amet consectetur adipisicing elit.
              </p>
            </div>
          </div>
          <div class="benefits__item">
            <div class="benefits__item-icon">
              <img src="../assets/images/icons/factory.svg" alt="factory" />
            </div>
            <div class="benefits__item-body">
              <div class="benefits__item-title">Quality maintain</div>
              <p class="benefits__item-text">
                Lorem ipsum dolor sit amet consectetur adipisicing elit.
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>
    <section class="top-products">
      <div class="container">
        <h2 class="section__title">Top Products</h2>
        <p class="section__text">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Corporis nulla reiciendis
          delectus quo.
        </p>
        <div class="top-products__slider-wrap">
          <div class="top-products__slider-buttons">
            <div class="swiper-button-prev"></div>
            <div class="swiper-button-next"></div>
          </div>
          <ProductsSlider
            :nav="{
              nextEl: '.swiper-button-next',
              prevEl: '.swiper-button-prev'
            }"
          />
        </div>
      </div>
    </section>
    <section class="questions">
      <div class="container">
        <h2 class="section__title">Frequently Asked Questions</h2>
        <p class="section__text">
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque diam pellentesque
          bibendum non dui volutpat fringilla bibendum.
        </p>
        <div class="loader" v-if="loader"></div>
        <div class="questions__list" v-if="questionsList.length && !loader">
          <Accordion v-for="(question, index) in questionsList" :key="index" :data="question" />
        </div>
      </div>
    </section>
    <SubscribeForm />
  </main>
</template>

<script>
import axios from 'axios'
import Banner from '../components/Banner.vue'
import ProductsSlider from '../components/ProductsSlider.vue'
import SubscribeForm from '../components/SubscribeForm.vue'
import Accordion from '../components/Accordion.vue'
export default {
  components: {
    Banner,
    ProductsSlider,
    SubscribeForm,
    Accordion
  },
  data() {
    return {
      questionsList: [],
      baseUrl: '',
      loader: false
    }
  },
  mounted() {
    const originPath = window.location.origin
    const basePath = this.$router.options.history.base
    this.baseUrl = originPath + basePath
    this.getQuestionsList()
  },
  methods: {
    getQuestionsList() {
      const self = this
      self.loader = true
      axios
        .get(self.baseUrl + '/mocks/questionsList.json')
        .then((response) => {
          self.questionsList = response.data
        })
        .catch((error) => {
          console.log(error)
        })
        .finally(() => {
          setTimeout(() => {
            self.loader = false
          }, 2000)
        })
    }
  }
}
</script>
