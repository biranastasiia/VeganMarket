<template>
  <div class="modal" v-if="modal_name">
    <div class="modal__bg" @click="closeModal"></div>
    <div class="modal__content">
      <component :is="modal_list[modal_name]" />
      <div class="modal__close" @click="closeModal"></div>
    </div>
  </div>
</template>

<script>
import { markRaw } from 'vue'
import ModalLogin from './ModalLogin.vue'
import ModalRegistration from './ModalRegistration.vue'
import ModalPwdRecovery from './ModalPwdRecovery.vue'

export default {
  components: {
    ModalLogin
  },
  data() {
    return {
      modal_name: null,
      modal_list: {
        login: markRaw(ModalLogin),
        registration: markRaw(ModalRegistration),
        pwd_recovery: markRaw(ModalPwdRecovery)
      }
    }
  },
  methods: {
    openModal(name) {
      const body = document.querySelector('body')
      body.style.overflow = 'hidden'
      this.modal_name = name
    },
    closeModal() {
      const body = document.querySelector('body')
      body.style.overflow = 'scroll'
      this.modal_name = null
    }
  }
}
</script>
