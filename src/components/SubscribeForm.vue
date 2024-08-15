<template>
  <section class="subscribe">
    <div class="container">
      <h2 class="section__title">Subscribe to our news and special offers</h2>
      <div class="subscribe__form" v-if="!success_msg">
        <div class="input-wrapper">
          <input
            class="input-field"
            v-model="email"
            :class="{ error: v$.email.$errors.length }"
            type="email"
            placeholder="Email"
          />
          <div class="input-errors" v-for="error of v$.email.$errors" :key="error.$uid">
            <div class="input-error-msg">{{ error.$message }}</div>
          </div>
        </div>
        <button class="cta-button subscribe__button" @click="submitForm()">
          <img src="../assets/images/icons/paper_plane.svg" alt="paper_plane" />
          <span class="subscribe__button-text">subscribe</span>
        </button>
      </div>
      <div class="registration__success" v-if="success_msg">
        <div class="registration__title">Thank you for subscription!</div>
        <div class="registration__link" @click="goToCatalog()">Let's go shopping!</div>
      </div>
    </div>
  </section>
</template>

<script>
import { useVuelidate } from '@vuelidate/core'
import { required, email } from '@vuelidate/validators'

export default {
  setup() {
    return { v$: useVuelidate() }
  },
  data() {
    return {
      email: '',
      success_msg: false
    }
  },
  validations() {
    return {
      email: { required, email }
    }
  },
  methods: {
    async submitForm() {
      const isFormCorrect = await this.v$.$validate()
      if (isFormCorrect) {
        this.success_msg = true
      }
    },
    goToCatalog() {
      this.$router.push('/catalog')
    }
  }
}
</script>
