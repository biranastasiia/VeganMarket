<template>
  <div class="registration">
    <div class="registration__title">Login</div>
    <form action="post" class="registration__form">
      <input class="registration__input" type="email" placeholder="email" />
      <input class="registration__input" type="password" placeholder="password" />
      <button class="registration__button cta-button" type="submit">Login</button>
    </form>
    <div class="registration__row">
      <div class="registration__link" @click="openModal('registration')">Registration</div>
      <div class="registration__link" @click="openModal('pwd_recovery')">Forget Password</div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    openModal(name) {
      this.$root.$refs.modal.openModal(name)
    }
  }
}
</script>
