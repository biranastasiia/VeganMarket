<template>
  <div class="cart">
    <div class="cart__header">
      <div class="cart__title">Cart</div>
      <div class="cart__close" @click="closeCart"></div>
    </div>
    <div class="cart__list" v-if="!isCartEmpty">
      <div class="cart__item" v-for="item in cartList" :key="item">
        <div class="cart__item-image">
          <img :src="baseUrl + item.image" :alt="item.title" />
        </div>
        <div class="cart__item-content">
          <div class="cart__item-row">
            <span class="cart__item-key">Title:</span>
            <span class="cart__item-value">{{ item.title }}</span>
          </div>
          <div class="cart__item-row">
            <span class="cart__item-key">Price per 1 item:</span>
            <span class="cart__item-value">${{ item.price }}</span>
          </div>
          <div class="cart__item-row">
            <span class="cart__item-key">Count:</span>
            <span class="cart__item-value">{{ item.count }}</span>
          </div>
          <div class="cart__item-row">
            <span class="cart__item-key">Total:</span>
            <span class="cart__item-value">${{ item.count * item.price }}</span>
          </div>
        </div>
      </div>
    </div>
    <div class="cart__footer" v-if="!isCartEmpty">
      <div class="cart__title">Total sum:</div>
      <div class="cart__title lato-font">${{ totalSum }}</div>
    </div>
    <div class="cart__empty" v-if="isCartEmpty">Your cart is empty</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      cartList: {},
      isCartEmpty: true,
      totalSum: 0,
      baseUrl: ''
    }
  },
  mounted() {
    const originPath = window.location.origin
    const basePath = this.$router.options.history.base
    this.baseUrl = originPath + basePath
    this.getCartList()
  },
  methods: {
    getCartList() {
      let cartStorage = localStorage.getItem('cart')
      if (cartStorage) {
        this.cartList = JSON.parse(cartStorage)
        this.calculateSum()
        this.isCartEmpty = false
      } else {
        this.cartList = {}
        this.isCartEmpty = true
      }
    },
    closeCart() {
      this.$parent.toggleCart()
    },
    calculateSum() {
      for (let item in this.cartList) {
        this.totalSum += this.cartList[item].count * this.cartList[item].price
      }
    }
  }
}
</script>
