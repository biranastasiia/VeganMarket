<template>
  <div class="registration">
    <div class="registration__title">Password recovery</div>
    <form action="post" class="registration__form">
      <input class="registration__input" type="email" placeholder="email" />
      <button class="registration__button cta-button" type="submit">Send</button>
    </form>
    <div class="registration__row">
      <div class="registration__link" @click="openModal('registration')">Registration</div>
      <div class="registration__link" @click="openModal('login')">Log in</div>
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
