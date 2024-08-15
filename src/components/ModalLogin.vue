<template>
  <div class="registration" v-if="!success_msg">
    <div v-if="fail_msg" class="registration__fail">
      <div>User doesn't exist</div>
      <div class="registration__link" @click="openModal('registration')">Registration</div>
      <div @click="fail_msg = !fail_msg" class="registration__fail-close"></div>
    </div>
    <div class="registration__title">Login</div>
    <div class="registration__form">
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
      <div class="input-wrapper">
        <div class="password-toggler" @click="isShown = !isShown">
          <img :class="{ visible: isShown }" src="../assets/images/icons/show.svg" alt="show" />
          <img
            :class="{ visible: !isShown }"
            src="../assets/images/icons/hidden.svg"
            alt="hidden"
            placeholder="Password"
          />
        </div>
        <input
          class="input-field"
          v-model="password"
          :class="{ error: v$.password.$errors.length }"
          :type="isShown ? 'text' : 'password'"
        />
        <div class="input-errors" v-for="error of v$.password.$errors" :key="error.$uid">
          <div class="input-error-msg">{{ error.$message }}</div>
        </div>
      </div>
      <button class="registration__button cta-button" @click="submitForm()">Login</button>
    </div>
    <div class="registration__bottom-line">
      <div class="registration__link" @click="openModal('registration')">Registration</div>
      <div class="registration__link" @click="openModal('pwd_recovery')">Forget Password</div>
    </div>
  </div>
  <div class="registration__success" v-if="success_msg">
    <div class="registration__title">Welcome, {{ name }}!</div>
    <div class="registration__link" @click="goToCatalog()">Let's go shopping!</div>
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
      name: '',
      email: '',
      password: '',
      isShown: false,
      success_msg: false,
      fail_msg: false
    }
  },
  validations() {
    return {
      email: { required, email },
      password: { required, minLength: minLength(8) }
    }
  },
  methods: {
    openModal(name) {
      this.$root.$refs.modal.openModal(name)
    },
    async submitForm() {
      const isFormCorrect = await this.v$.$validate()
      if (isFormCorrect) {
        const savedUser = JSON.parse(localStorage.getItem('user'))

        if (savedUser && savedUser.email === this.email && savedUser.password === this.password) {
          this.name = savedUser.name
          this.success_msg = true
          localStorage.setItem('login', true)
        } else {
          this.fail_msg = true
        }
      }
    },
    goToCatalog() {
      this.$root.$refs.modal.closeModal()
      this.$router.push('/catalog')
      //   location.href = '/catalog'
    }
  }
}
</script>
