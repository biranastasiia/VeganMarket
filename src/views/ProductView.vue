<template>
  <div class="product-page">
    <section class="product">
      <div class="container">
        <h1 class="product__title">{{ productData.title }}</h1>
        <div class="product__body">
          <div class="product__gallery">
            <Gallery
              :list="productData.gallery"
              :title="productData.title"
              :is_new="productData.is_new"
              :discount="productData.discount"
            />
          </div>
          <div class="product__content">
            <p class="product__description">{{ productData.description }}</p>
            <div class="product__price">
              <div class="product__price-current">${{ productData.price }}</div>
              <div class="product__price-old" v-if="productData.old_price">
                ${{ productData.old_price }}
              </div>
            </div>
            <div class="product__count">
              <div class="product__count-title">Add to cart:</div>
              <div class="product__count-buttons">
                <div
                  class="product__count-button product__count-remove"
                  :class="{ disabled: count === 0 }"
                  @click="removeFromCart"
                >
                  &dash;
                </div>
                <div class="product__count-button product__count-count">{{ count }}</div>
                <div
                  class="product__count-button product__count-add"
                  :class="{ disabled: count === productData.stock }"
                  @click="addToCart"
                >
                  &plus;
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="top-products">
      <div class="container">
        <h2 class="section__title">See also:</h2>
        <div class="top-products__slider-wrap">
          <div class="top-products__slider-buttons">
            <div class="swiper-button-prev"></div>
            <div class="swiper-button-next"></div>
          </div>
          <ProductsSlider
            ref="productsSlider"
            :nav="{
              nextEl: '.swiper-button-next',
              prevEl: '.swiper-button-prev'
            }"
          />
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import axios from 'axios'
import ProductsSlider from '../components/ProductsSlider.vue'
import Gallery from '../components/Gallery.vue'

export default {
  components: {
    ProductsSlider,
    Gallery
  },
  data() {
    return {
      productData: {},
      count: 0
    }
  },
  mounted() {
    this.getProduct()
    ProductsSlider.methods.getProductsList()
    // this.$refs.productsSlider.getProductsList()
  },
  watch: {
    $route(to, from) {
      this.getProduct()
    }
  },
  methods: {
    getProduct() {
      const self = this
      const productId = this.$route.params.id - 1
      //   this.loader = true

      axios
        .get('./mocks/productsList.json')
        .then(function (response) {
          self.productData = response.data[productId]
          //   self.loader = false
        })
        .catch(function (error) {
          console.log(error, 'error')
          //   self.loader = false
        })
    },
    removeFromCart() {
      if (this.count > 0) {
        this.count--
        this.setCart()
      }
    },
    addToCart() {
      if (this.count < this.productData.stock) {
        this.count++
        this.setCart()
      }
    },
    setCart() {
      let cartStorage = localStorage.getItem('cart')
      if (cartStorage) {
        cartStorage = JSON.parse(cartStorage)
      } else {
        cartStorage = {}
      }

      if (this.count === 0) {
        delete cartStorage[this.productData.title]
      } else {
        this.productData.count = this.count
        cartStorage[this.productData.title] = this.productData
      }

      localStorage.setItem('cart', JSON.stringify(cartStorage))
    }
  }
}
</script>
