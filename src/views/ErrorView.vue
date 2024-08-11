<template>
  <div class="error-view">
    <h2 class="error-view__title">Oops! Page not found.</h2>
    <RouterLink class="error-view__link" to="/">Back home</RouterLink>
  </div>
</template>

<script>
import { RouterLink } from 'vue-router'

export default {
  components: {
    RouterLink
  }
}
</script>
