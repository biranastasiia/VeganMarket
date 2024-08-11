<template>
  <RouterLink :to="'/product/' + data.id" class="product-card">
    <div class="product-card__image-wrap">
      <div class="product-card__signs">
        <div class="product-card__sign discount" v-if="data.discount">sale</div>
        <div class="product-card__sign new" v-if="data.is_new">new</div>
      </div>
      <img class="product-card__image" :src="data.image" :alt="data.title" />
    </div>
    <div class="product-card__body">
      <div class="product-card__title">{{ data.title }}</div>
      <p class="product-card__description">{{ data.description }}</p>
      <div class="product-card__price">
        ${{ data.price }}
        <sup class="product-card__old-price" v-if="data.old_price">${{ data.old_price }}</sup>
      </div>
    </div>
  </RouterLink>
</template>

<script>
import { RouterLink } from 'vue-router'

export default {
  props: ['data'],
  components: {
    RouterLink
  },
  data() {
    return {}
  }
}
</script>
