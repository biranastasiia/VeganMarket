<template>
  <header class="header" :class="{ fixed: isFixed }">
    <div class="container">
      <RouterLink to="/" class="logo">VeganMarket</RouterLink>
      <nav class="header__nav">
        <div class="header__nav-burger" @click="toggleMenu()">
          <div></div>
        </div>
        <div class="header__nav-wrap" v-if="isMenu">
          <div class="header__nav-close" @click="isMenu = false"></div>
          <ul class="header__nav-list">
            <li class="header__nav-item">
              <RouterLink to="/">Home</RouterLink>
            </li>
            <li class="header__nav-item">
              <RouterLink to="/about">About us</RouterLink>
            </li>
            <li class="header__nav-item">
              <RouterLink to="/catalog">Products Catalog</RouterLink>
            </li>
            <li class="header__nav-item">
              <RouterLink to="/blog">News Blog</RouterLink>
            </li>
            <li class="header__nav-item">
              <RouterLink to="/contacts">Contact us</RouterLink>
            </li>
          </ul>
        </div>
      </nav>
      <div class="header__icons">
        <div class="header__icon" @click="openModal('login')">
          <img src="../assets/images/icons/user.svg" alt="user" />
        </div>
        <div class="cart__wrap">
          <div class="header__icon" @click="toggleCart()">
            <img src="../assets/images/icons/cart.svg" alt="user" />
          </div>
          <Cart v-if="isCart" />
        </div>
      </div>
    </div>
  </header>
</template>

<script>
import { RouterLink } from 'vue-router'
import Cart from './Cart.vue'

export default {
  components: {
    RouterLink,
    Cart
  },
  data() {
    return {
      isFixed: false,
      isCart: false,
      isMenu: true
    }
  },
  mounted() {
    window.addEventListener('resize', () => {
      if (window.innerWidth > 768) {
        this.isMenu = true
      } else {
        this.isMenu = false
      }
    })
    window.addEventListener('scroll', () => {
      if (window.scrollY > 50) {
        this.isFixed = true
      } else {
        this.isFixed = false
      }
    })
  },
  methods: {
    openModal(name) {
      this.$root.$refs.modal.openModal(name)
    },
    toggleCart() {
      this.isCart = !this.isCart
    },
    toggleMenu() {
      this.isMenu = !this.isMenu
    }
  }
}
</script>
