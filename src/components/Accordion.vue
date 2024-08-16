<template>
  <div class="accordion" :class="{ active: isActive }">
    <div class="accordion__header">
      <div class="accordion__title">{{ data.question }}</div>
      <div class="accordion__close" @click="toggleAccordion()"></div>
    </div>
    <div class="accordion__body">{{ data.answer }}</div>
  </div>
</template>

<script>
export default {
  props: ['data'],
  data() {
    return {
      isActive: false
    }
  },
  methods: {
    toggleAccordion() {
      this.isActive = !this.isActive
      const accordionBody = this.$el.querySelector('.accordion__body')

      if (this.isActive) {
        accordionBody.style.height = accordionBody.scrollHeight + 15 + 'px'
      } else {
        accordionBody.style.height = '0px'
      }
    }
  }
}
</script>
