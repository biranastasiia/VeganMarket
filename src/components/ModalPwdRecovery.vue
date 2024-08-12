<template>
  <div class="registration">
    <div class="registration__title">Password recovery</div>
    <div class="registration__form">
      <div class="input-wrapper">
        <input
          class="input-field"
          v-model="email"
          :class="{ error: v$.email.$errors.length }"
          type="email"
        />
        <div class="input-errors" v-for="error of v$.email.$errors" :key="error.$uid">
          <div class="input-error-msg">{{ error.$message }}</div>
        </div>
      </div>
      <button class="registration__button cta-button" @click="submitForm()">Send</button>
    </div>
    <div class="registration__bottom-line">
      <div class="registration__link" @click="openModal('registration')">Registration</div>
      <div class="registration__link" @click="openModal('login')">Log in</div>
    </div>
  </div>
</template>

<script>
import { useVuelidate } from '@vuelidate/core'
import { required, email, minLength } from '@vuelidate/validators'

export default {
  setup() {
    return { v$: useVuelidate() }
  },
  data() {
    return {
      email: ''
    }
  },
  validations() {
    return {
      email: { required, email }
    }
  },
  methods: {
    openModal(name) {
      this.$root.$refs.modal.openModal(name)
    },
    async submitForm() {
      const isFormCorrect = await this.v$.$validate()
      if (isFormCorrect) {
        console.log('fine')
      }
    }
  }
}
</script>
