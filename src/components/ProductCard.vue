<template>
  <RouterLink :to="'/product/' + product.id" class="product-card">
    <div class="product-card__image-wrap">
      <div class="product-card__signs">
        <div class="product-card__sign discount" v-if="product.discount">sale</div>
        <div class="product-card__sign new" v-if="product.is_new">new</div>
      </div>
      <img class="product-card__image" :src="baseUrl + product.image" :alt="product.title" />
    </div>
    <div class="product-card__body">
      <div class="product-card__title">{{ product.title }}</div>
      <p class="product-card__description">{{ product.description }}</p>
      <div class="product-card__price lato-font">
        ${{ product.price }}
        <sup class="product-card__old-price" v-if="product.old_price">${{ product.old_price }}</sup>
      </div>
    </div>
  </RouterLink>
</template>

<script>
import { RouterLink } from 'vue-router'

export default {
  props: ['product'],
  components: {
    RouterLink
  },
  data() {
    return {
      baseUrl: ''
    }
  },
  mounted() {
    const originPath = window.location.origin
    const basePath = this.$router.options.history.base
    this.baseUrl = originPath + basePath
  }
}
</script>
