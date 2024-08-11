<template>
  <div class="registration">
    <div class="registration__title">Registration</div>
    <form action="post" class="registration__form">
      <input class="registration__input" type="text" placeholder="name" />
      <input class="registration__input" type="email" placeholder="email" />
      <input class="registration__input" type="password" placeholder="password" />
      <input class="registration__input" type="password" placeholder="repeat password" />
      <button class="registration__button cta-button" type="submit">Register</button>
    </form>
    <div class="registration__row">
      <div class="registration__link" @click="openModal('login')">Log in</div>
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
