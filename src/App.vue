<template>
  <Header />
  <main>
    <RouterView />
  </main>
  <Footer />
  <Modal ref="modal" />
</template>

<script setup>
import Header from './components/Header.vue'
import Modal from './components/Modal.vue'
import Footer from './components/Footer.vue'
import { RouterView } from 'vue-router'
</script>
