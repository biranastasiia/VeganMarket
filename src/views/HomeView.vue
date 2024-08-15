<template>
  <main>
    <Banner />
    <section class="benefits">
      <div class="container">
        <h2 class="section__title">Why Us?</h2>
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
    <SubscribeForm />
  </main>
</template>

<script>
import Banner from '../components/Banner.vue'
import ProductsSlider from '../components/ProductsSlider.vue'
import SubscribeForm from '../components/SubscribeForm.vue'
export default {
  components: {
    Banner,
    ProductsSlider,
    SubscribeForm
  }
}
</script>
