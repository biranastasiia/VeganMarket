<template>
  <div class="registration" v-if="!success_msg">
    <div class="registration__title">Registration</div>
    <div class="registration__form">
      <div class="input-wrapper">
        <input
          class="input-field"
          v-model="name"
          :class="{ error: v$.name.$errors.length }"
          type="text"
          placeholder="First name"
        />
        <div class="input-errors" v-for="error of v$.name.$errors" :key="error.$uid">
          <div class="input-error-msg">{{ error.$message }}</div>
        </div>
      </div>
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
          placeholder="Confirm password"
        />
        <div class="input-errors" v-for="error of v$.password.$errors" :key="error.$uid">
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
          />
        </div>
        <input
          class="input-field"
          v-model="password_copy"
          :class="{ error: v$.password_copy.$errors.length }"
          :type="isShown ? 'text' : 'password'"
        />
        <div class="input-errors" v-for="error of v$.password_copy.$errors" :key="error.$uid">
          <div class="input-error-msg">{{ error.$message }}</div>
        </div>
      </div>
      <button class="registration__button cta-button" @click="submitForm()">Register</button>
    </div>
    <div class="registration__bottom-line">
      <div class="registration__link" @click="openModal('login')">Log in</div>
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
import { required, email, minLength, sameAs } from '@vuelidate/validators'
export default {
  setup() {
    return { v$: useVuelidate() }
  },
  data() {
    return {
      name: '',
      email: '',
      password: '',
      password_copy: '',
      isShown: false,
      success_msg: false
    }
  },
  validations() {
    return {
      name: { required },
      email: { required, email },
      password: { required, minLength: minLength(8) },
      password_copy: { required, sameAsPassword: sameAs(this.password) }
    }
  },
  methods: {
    openModal(name) {
      this.$root.$refs.modal.openModal(name)
    },
    async submitForm() {
      const isFormCorrect = await this.v$.$validate()
      if (isFormCorrect) {
        this.success_msg = true
        const userData = {
          name: this.name,
          email: this.email,
          password: this.password
        }
        localStorage.setItem('user', JSON.stringify(userData))
        localStorage.setItem('login', true)
      }
    },
    goToCatalog() {
      this.$root.$refs.modal.closeModal()
      this.$router.push('/catalog')
    }
  }
}
</script>
